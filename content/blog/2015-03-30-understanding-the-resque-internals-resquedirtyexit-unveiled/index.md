---
title: "Understanding the Resque internals - Resque::DirtyExit unveiled"
date: 2015-03-30
categories: 
  - "article"
tags: 
  - "opensource"
  - "resque"
  - "ruby"
---

If your **Resque jobs** fail because of a mysterious `Resque::DirtyExit` a quick tour of the Resque internals will help you fix the issue and be back up and running in a matter of minutes.

<!--more-->

## The Problem

**TL;DR**: Reduce the number of workers. Make smaller jobs.

Recently I had to import some data from a MySQL database into a Redis store for further processing. The MySQL database contains time-series data and the natural approach to run the import was to split the time window into smaller chunks and each chunk is handled by one Resque job.

![](images/Resque-Dirty-Failure-Blog-post-New-Page.png)

Each job processes 1 hour of data and there are 12 workers picking them. After 1 day I opened the Resque console and I saw that more than 50% of my jobs failed:

```
[1] pry(main)> Resque.info
=> {:pending=>292, :processed=>619, :queues=>1, :workers=>12, :working=>12, :failed=>344, :servers=>["redis://127.0.0.1:6379/0"], :environment=>"staging8"}
```

and this is the error:

```
[3] pry(main)> Resque::Failure.all(1,1)
=> {"failed_at"=>"2015/03/28 10:24:18 UTC",
 "payload"=>{"class"=>"Jobs::ImportTimeRange", "args"=>[{"time_range"=>"2015-02-22T01:00:00+00:00..2015-02-22T02:00:00+00:00"}]},
 "exception"=>"Resque::DirtyExit",
 "error"=>"pid 18535 SIGKILL (signal 9)",
 "backtrace"=>[],
 "worker"=>"staging8:12851:*",
 "queue"=>"my_import"}
```

A puzzling piece was that my logger was not able to catch the error even if the entire job was wrapped in a `begin/rescue` block, like this:

```
module Jobs
  class ImportTimeRange
    @queue = :my_import
    
    class << self       
      def perform(opts)
        @time_range = opts.fetch('time_range')
        logger.info("[Starting] ImportTimeRange #{opts.to_s}")           
        # Do the job
        logger.info("[Completed] ImportTimeRange #{opts.to_s}")         
        
        rescue Exception => e
          logger.error("[Failed] ImportTimeRange #{opts.to_s}: #{e.to_s}")
          raise e
      end
      
      private
      
      def logger
        @logger ||= # give me a logger
      end
    end
  end
end
```

## The Resque internals

To understand what was going on I decided to open the Resque code. In the `Resque::ChildProcess` class you can see the following:

```
# @param job [Resque::Job]
# @return [void]
# @yieldparam (see Resque::Worker#perform)
# @yieldreturn (see Resque::Worker#perform)
def fork_and_perform(job, &block)
  @pid = fork(job) do
    child_job(job, &block)
  end

  if @pid
    wait
    job.fail(DirtyExit.new($?.to_s)) if $?.signaled?
  else
    worker.perform(job, &block)
  end
end

```

When the job is picked up a new process is created with `fork`. The child process goes ahead and executes the job. The parent simply waits for the child process to finish.

This is where the `DirtyExit` error comes into play. First of all let's have a look in detail at `$?.signaled?`. From the Ruby core documentation we have:

```
# Status of last executed child process.
# This variable is thread local and read-only.
$? = Process::Status.new #value is unknown, used for indexing.
```

```
# stat.signaled?   -> true or false
#  
# Returns +true+ if _stat_ terminated because of
# an uncaught signal.
def signaled?()
  #This is a stub, used for indexing
end
```

The child process in charge of processing the job was killed by someone who is not Resque itself. Maybe the Linux Kernel? Maybe a bad sysadmin? I don't know.

## The Solution

At this point it was clear that: \* Resque was simply noticing that my Job processes were being killed and was kind enough to write it for me on Redis (the Resque backend). \* My job processes were being killed with SIGKILL. With such signal the receiving process cannot perform any clean-up before quitting, not even the error logging of my initial example.

Pretty sad eh?

At this point my only suspect left was resources, and maybe the operating system killing my workers because of that. I decided to go ahead and validate this assumption by _making smaller things_ (citing S. Metz).

Here is what I did: \* **Reduce the import window from 1 hour to 15 minutes.** \* **Reduce the workers from 12 to 4.**

The result is surprisingly good. I went from a 50% failure rate, to zero:

```
[2] pry(main)> Resque.info
=> {:pending=>3352, :processed=>196, :queues=>1, :workers=>4, :working=>4, :failed=>0, :servers=>["redis://127.0.0.1:6379/0"], :environment=>"staging8"}
```

## Conclusion

Your jobs may be failing because of **(i) software errors or (ii) infrastructure problems**. We usually focus on the former, but never forget about checking that your hardware is doing fine.

Also, opening the Resque gem helped me find the information I needed pretty quickly. I'll do it more often, it is also a chance to learn something new. The quick solution of googling for the error gave me no extra insights in this case.

Looking forward to hearing from you in the comments and if you like the blog please consider adding it to your feed or follow me on Twitter.
