---
title: "Not So Random Software #32 - Confidence and decrypting cookies"
date: 2020-07-01
categories: 
  - "newsletter"
tags: 
  - "browsers"
  - "cookies"
  - "humanbiases"
  - "learning"
  - "memory"
  - "webdevelopment"
---

Hello everyone and welcome back to Not So Random Software!

This week's links are about confidence, and how to avoid being fooled by it. Lastly, we are going to jump into the world of browser cookie decryption, something I dealt with it recently.

Enjoy the random walk!

## A random article or paper

Don't blink; the hazards of confidence

I sometimes receive comments from self-proclaimed experts on (hard) topic X who claim they figured it out. As a former scientist, I am deeply skeptical of quick recipes for success, so is Nobel prize Daniel Kahneman in this New York Times article.

## A random video or podcast

Developing Expertire - Dave Thomas

In this presentation made during QCon 2007, Dave Thomas talks about expanding people's expertise in their domains of interest by not treating them uniformly as they had the same amount of knowledge and level of experience.

## A random book

Make it stick: the science of successful learning

New insights into how memory is encoded, consolidated, and later retrieved have led to a better understanding of how we learn. This book is a marvelous read for those interested in the challenge of lifelong learning and self-improvement.

## A random tool

Cookie decryptor gem

If you are looking for a way to decrypt your cookies in Rails, this gem summarises how it's done by extracting the relevant code into a reusable class. Paste an encrypted cookie value, get the decrypted hash back. Actually didn't work for me, so it needs some configuration, but it's a great place to start.

## A random line of code

If you prefer a shorter version of the above gem, this is what I recently extracted out by navigating that same codebase.

```
def rails_cookie_decrypt(cookie)
  cookie = CGI::unescape(cookie)
  # a wrapper for your Rails secrets to generate internal keys
  key_generator = Rails.application.key_generator

  # the default cypher for the latest rails, it might be different for you
  encrypted_cookie_cipher = "aes-256-gcm"

  # default string used by Rails as a salt
  authenticated_encrypted_cookie_salt = "authenticated encrypted cookie"

  # generate the encryption secret from your application global secret
  key_len = ActiveSupport::MessageEncryptor.key_len(encrypted_cookie_cipher)
  secret = key_generator.generate_key(authenticated_encrypted_cookie_salt, key_len)

  # the rails wrapper for OpenSSL::Cipher in the Ruby standard library
  encryptor = ActiveSupport::MessageEncryptor.new(secret, cipher: encrypted_cookie_cipher, serializer: ActiveSupport::MessageEncryptor::NullSerializer)

  # decrypt using the cookie as as a purpose, you can find the name by looking at the storage in your browser
  encryptor.decrypt_and_verify(cookie, purpose: 'cookie._your_cookie_name')
end
```

## A random quote

> True intuitive expertise is learned from prolonged experience with good feedback on mistakes. You are probably an expert in guessing your spouse’s mood from one word on the telephone; chess players find a strong move in a single glance at a complex position; and true legends of instant diagnoses are common among physicians. To know whether you can trust a particular intuitive judgment, there are two questions you should ask: Is the environment in which the judgment is made sufficiently regular to enable predictions from the available evidence? The answer is yes for diagnosticians, no for stock pickers. Do the professionals have an adequate opportunity to learn the cues and the regularities? The answer here depends on the professionals’ experience and on the quality and speed with which they discover their mistakes.
> 
> Daniel Kahneman

## Receive this by email

\* indicates required

Email Address \*  
  

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

<script type="text/javascript">(function($) {window.fnames = new Array(); window.ftypes = new Array();fnames[0]='EMAIL';ftypes[0]='email';fnames[1]='FNAME';ftypes[1]='text';fnames[2]='LNAME';ftypes[2]='text';fnames[3]='ADDRESS';ftypes[3]='address';fnames[4]='PHONE';ftypes[4]='phone';fnames[5]='BIRTHDAY';ftypes[5]='birthday';}(jQuery));var $mcj = jQuery.noConflict(true);</script>
