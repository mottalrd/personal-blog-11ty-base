---
title: "Data manipulation primitives in R and Python"
date: 2015-07-26
categories: 
  - "article"
tags: 
  - "data-analysis"
  - "python"
  - "r"
---

Both R and Python are incredibly good tools to manipulate your data and their integration is becoming increasingly important\[note\]IEEE 2015 top programming languages\[/note\]. The latest tool for data manipulation in R is Dplyr\[note\]Dplyr homepage\[/note\] whilst Python relies on Pandas\[note\]Pandas homepage\[/note\].

In this blog post I'll show you the fundamental primitives to manipulate your dataframes using both libraries highlighting their major advantages and disadvantages.

<!--more-->

## Theory first

Data Frames are basically tables. Codd, E.F. in 1970 defined Relational algebra\[note\]Relational Algebra\[/note\] as the basic the theory to work on relational tables. It defines the following operations:

- Projection (π)
- Selection (σ)
- Rename (ρ)
- Set operators (union, difference, cartesian product)
- Natural join (⋈)

SQL dialects also added the following

- Aggregations
- Group by operations

Why we care? People redefined these basic operations over and over in the last 40 years starting with SQL until today latest query languages. This framework will give us a general language independent perspective on the data manipulation.

## Hands on

I will use the nycflights13 dataset used to introduce dplyr\[note\]NYC Flights 2013 dataset\[/note\] to present the functions. If you are interested you can download this entire blog post as an IPython notebook. Let's initialise our environment first:

```
# Load the R magic command
%load_ext rpy2.ipython
from rpy2.robjects import pandas2ri

# numpy available as np
# pyplot available as ply
%pylab

from pandas import *

Using matplotlib backend: MacOSX
Populating the interactive namespace from numpy and matplotlib

%%R -o flights
#sink(type="output")
sink("/dev/null")
library("dplyr");
library(nycflights13);

flights = pandas2ri.ri2py(flights)
```

## Data summary

In both libraries it is possible to quickly print a quick summary of your dataframe. Pandas has an object oriented approach and you can invoke `head()`, `tail()` and `describe()` directly on your dataframe object. R has a procedural approach and its functions take a dataframe as the first input.

| Python | R |
| --- | --- |
| `df.head()` | `head(df)` |
| `df.tail()` | `tail(df)` |
| `df.describe()` | `summary(df)` |

```
# Python

flights.head();
flights.tail();
flights.describe();

%R head(flights);
%R tail(flights);
%R summary(flights);
```

## Selection

In pandas in order to select multiple rows you need to use the `[]` operator with the element-wise operators like `&` and `|`. If you don't use the element-wise operators you will get the following error: `ValueError: The truth value of a Series is ambiguous`. Another solution is to install the numexpr\[note\]Numexpr python package\[/note\] package and use the `query()` function.

`dplyr` instead provides the `filter()` function. Combined with the pipe operator `%>%` the code is incredibly readable in my opinion. Notice how repeating the dataframe variable in the boolean expression is not needed in this case.

| Python | R |
| --- | --- |
| `df[bool expr with element-wise operators]` | `df %>% filter(bool expr)` |
| `df.query('bool expr')` |  |

```
# Python

# Simple filtering
flights[flights.month <= 3];

# Filtering with element-wise operators
flights[(flights.month >= 3) & (flights.month <= 6)];

# with numexpr
flights.query('month >= 3 & month <= 6');

%R flights %>% filter(month >= 3 & month <= 6);
```

## Projection

You can use the projection operation to extract one (or more) columns from a dataframe. In Python you pass an array with the columns you are interested in to the DataFrame object. In dplyr the projection function is called select, inspired by SQL.

| Python | R |
| --- | --- |
| `df[['col_1', 'col_2']]` | `df %>% select(col_1, col_2)` |

```
# Python
flights[['year', 'month']];

%R flights %>% select(month, year);
```

## Rename

The rename operation is used to simply rename a column of your dataframe keeping the content intact. In pandas you use the rename\[note\]pandas.DataFrame.rename\[/note\] function and you provide a dictionary. In R you use a comma separated list of assignments.

| Python | R |
| --- | --- |
| `df.rename(columns={'col_name': 'col_new_name'})` | `df %>% rename(col_new_name = col_name)` |

```
# Python
flights.rename(columns={'month': 'TheMonth'});

%R flights %>% rename(TheMonth = month);
```

## Union

The relational algebra uses set union, set difference, and Cartesian product from set theory, with the extra constraint that tables must be "compatible", i.e. they must have the same columns.

You can use the union in Pandas using the `concat()`\[note\]Merging data frames in Panda\[/note\] operation. You need to take some extra care for indexes though and for that I'll forward you to the docs\[note\]Concatenating objects in Pandas\[/note\].

In R you rely on the `bind_rows`\[note\]Dplyr bind function\[/note\] operator.

| Python | R |
| --- | --- |
| `concat([df_1, df_2]);` | `rbind_list(df_1, df_2)` |

```
# Python

df_1 = flights.query('dep_time == 518');
df_2 = flights.query('dep_time == 517');
concat([df_1, df_2]);

%%R
sink("/dev/null")
df_1 = filter(flights, dep_time == 517);
df_2 = filter(flights, dep_time == 518);
bind_rows(df_1, df_2);
```

## Difference

To the best of my knowledge there is no set difference operator in Python. In order to achieve the result we must rely on the select operator.

In dplyr there is a native operator `setdiff` that does exactly what we expect.

| Python | R |
| --- | --- |
| `set_a[~set_a.column.isin(set_b.column)]` | `set_a %>% setdiff(set_b)` |

```
# Python

set_a = flights.query('dep_time == 517 | dep_time == 518');
set_b = flights.query('dep_time == 518 | dep_time == 519');

selection = ~set_a.dep_time.isin(set_b.dep_time);
set_a[selection];

%%R
#sink(type="output")
#sink("/dev/null")
set_a = filter(flights, dep_time == 517 | dep_time == 518);
set_b = filter(flights, dep_time == 518 | dep_time == 519);
set_a %>% setdiff(set_b)
```

## Cartesian product

You can use the cartesian product to combine two tables with a disjoint set of columns. In practice this is not a very common operation and as a result both libraries lack a pure cartesian product (in favour of the way more common `join` operator).

A simple trick to overcome this limitation is to create a temporary column first, perform the join and finally remove the temporary column. This can be done both in Python and R using the `merge()` and `full_join` methods.

| Python | R |
| --- | --- |
| `merge(...) with tmp column` | `full_join(...) with tmp column` |

```
# Python

df_1 = DataFrame({
        'name': ['Jack', 'Mario', 'Luigi']
    });
df_2 = DataFrame({
        'surname': ['Rossi', 'Verdi', 'Reacher']
    });

df_1['tmp'] = np.nan;
df_2['tmp'] = np.nan;

merge(df_1, df_2, on='tmp').drop('tmp', axis=1);

%%R
#sink(type="output")
sink("/dev/null")
df_1 = data.frame(
    name=c('Jack', 'Mario', 'Luigi'),
    stringsAsFactors=FALSE)

df_2 = data.frame(
    surname=c('Rossi', 'Verdi', 'Reacher'), 
    stringsAsFactors=FALSE)

df_1$tmp = NA
df_2$tmp = NA

full_join(df_1, df_2, by="tmp") %>% select(-tmp)
```

## Natural Join

If you are used to SQL you are definitely aware of what a join operation is. Given two dataframe R and S the result of the natural join is the set of all combinations of tuples in R and S that are equal on their common attribute names.

In Python you can rely on the very powerful merge\[note\]Pandas merge function\[/note\] command. In R Dplyr you can use the full\_join\[note\]Dplyr documentation\[/note\] command.

| Python | R |
| --- | --- |
| `merge(..., on="key", how="outer")` | `full_join(..., by="key")` |

```
# Python
df_1 = DataFrame({
        'name': ['Jack', 'Mario', 'Luigi'],
        'department_id' : [30, 31, 31]
    });
df_2 = DataFrame({
        'department_name': ['Sales', 'Product', 'Finance'],
        'department_id' : [30, 31, 32]
    });

merge(df_1, df_2, on="department_id", how="outer");

%%R
#sink(type="output")
sink("/dev/null")

df_1 = data.frame(
    name=c('Jack', 'Mario', 'Luigi'),
    department_id=c(30, 31, 31),
    stringsAsFactors=FALSE)

df_2 = data.frame(
    department_name=c('Sales', 'Product', 'Finance'), 
    department_id=c(30, 31, 32),
    stringsAsFactors=FALSE)

full_join(df_1, df_2, by="department_id")
```

## Aggregations

An aggregate function is a function that takes the values of a certain column to form a single value of more significant meaning. Typical aggregate functions available in the most common SQL dialects include Average(), Count(), Maximum(), Median(), Minimum(), Mode(), Sum().

Both R and Python dataframes provides methods to extract this information. In this case I would say that Python handle missing values default better, whilst on R we have to provide `na.rm = TRUE`.

| Python | R |
| --- | --- |
| `df.<column>.mean()` | `summarise(df, test=mean(<column>, na.rm = TRUE))` |
| `df.<column>.median()` | `summarise(df, test=median(<column>, na.rm = TRUE))` |
| `df.<column>.std()` | `summarise(df, test=sd(<column>, na.rm = TRUE))` |
| `df.<column>.var()` | `summarise(df, test=var(<column>, na.rm = TRUE))` |
| `df.<column>.min()` | `summarise(df, test=min(<column>, na.rm = TRUE))` |
| `df.<column>.max()` | `summarise(df, test=max(<column>, na.rm = TRUE))` |

```
# Python 

flights.dep_time.mean();
flights.dep_time.median();
flights.dep_time.std();
flights.dep_time.var();
flights.dep_time.min();
flights.dep_time.max();
flights.dep_time.mean();

%%R
#sink(type="output")
sink("/dev/null")

summarise(flights, test=mean(dep_time, na.rm = TRUE))
summarise(flights, test=median(dep_time, na.rm = TRUE))
summarise(flights, test=min(dep_time, na.rm = TRUE))
summarise(flights, test=max(dep_time, na.rm = TRUE))
summarise(flights, test=sd(dep_time, na.rm = TRUE))
summarise(flights, test=var(dep_time, na.rm = TRUE))
```

## Group by

Aggregations become useful especially when used in conjunction with the group by operator. This way we are able to compute statistics for a number of group subsets with just one command.

Both Python and R provides the function to run a group by.

| Python | R |
| --- | --- |
| `df.groupby('<column>')` | `df %>% group_by(<column>)` |

```
# Python

# For any given day compute the mean of the flights departure time
flights.groupby('day').dep_time.mean();

%%R
#sink(type="output")
sink("/dev/null")

flights %>% 
    group_by(day) %>% 
    summarise(dep_time_mean=mean(dep_time, na.rm = TRUE))
```

## Conclusion

I think the Pandas and Dplyr paradigms are very different between each other.

Pandas is more focused on object orientation and good defaults. Indexes are a first class entity and as a result some operations that you expect to be simple are instead quite difficult to grasp.

Conversely Dplyr is procedural. I love the pipe operator and manipulating my data feels incredibly smooth. The only sad note is that sometimes functions defaults are not that great. I haven't tested the speed in this blog post but I assume that since indexes are hidden in Dplyr the speed is probably much lower in general.

In conclusion I feel like Dplyr and R are the perfect tool for some early exploration of the data. But if you are serious about the code you are producing you should probably switch to Python to productionise your data analysis.

Let me know your approach in the comments!

## References
