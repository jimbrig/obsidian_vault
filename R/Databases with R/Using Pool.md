---
creation date: 2021-05-04 22:46
modification date: Tuesday 4th May 2021 22:46:55
tags: ["#r", "#databases"]
author: Jimmy Briggs
---

# Using Pool vs. DBI

## Pool

Connection Methods:

1. `pool::poolCreate( ... )`
2. `pool::dbPool( ... )`

### poolCreate

```R
pool <- poolCreate(
  factory,
  minSize = 1,
  maxSize = Inf,
  idleTimeout = 60,
  validationInterval = 600,
  state = NULL
)
```

in conjunction with: `pool::poolClose(pool)`.

`poolCreate` is an **S4** class for compatibility with the `DBI` methods.



S4 class for compatibility with DBI methods
Description
A generic pool class that holds objects. These can be fetched

Usage
poolCreate(
  factory,
  minSize = 1,
  maxSize = Inf,
  idleTimeout = 60,
  validationInterval = 600,
  state = NULL
)

poolClose(pool)

## S4 method for signature 'Pool'
poolClose(pool)
Arguments
factory	
A factory function responsible for the generation of the objects that the pool will hold (ex: for DBI database connections, this function is dbConnect). It must take no arguments.

minSize	
An optional number specifying the minimum number of objects that the pool should have at all times.

maxSize	
An optional number specifying the maximum number of objects that the pool may have at any time.

idleTimeout	
The number of seconds that an idle object will be kept in the pool before it is destroyed (only applies if the number of objects is over the minSize). Use Inf if you want created objects never to be destroyed (there isn't a great reason for this usually).

validationInterval	
The minimum number of seconds that pool will wait before running a validation check on the next checked out object. By not necessarily validating every checked out object, there can be substantial performance gains (especially if the interval between checking out new objects is very small).

state	
A pool public variable to be used by backend authors as necessary.

pool	
A Pool object previously created with poolCreate

***
Links: 
Source:

