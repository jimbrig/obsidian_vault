---
creation date: 2021-05-04 22:46
modification date: Tuesday 4th May 2021 22:46:55
tags: ["#r", "#databases"]
author: Jimmy Briggs
---

# Using Pool, DBI, and Other Drivers

The R PAckage `pool` enables the creation of object pools, which make it less computationally expensive to fetch a new object. Currently the only supported pooled objects are 'DBI' connections.

## Pool

Connection Methods:

1. `pool::poolCreate( ... )`
2. `pool::dbPool( ... )`

### DBI Connection Methods:

As a convenience, Pool implements DBIConnection methods; calling any implemented DBI method directly on a Pool object will result in a connection being checked out (with `poolCheckout()`), the operation being performed on that connection, and the connection being returned to the pool (with `poolReturn()`).

Pool cannot implement the `DBI::dbSendQuery()` and `DBI::dbSendStatement()` methods because they both return live ResultSet objects. This is incompatible with the Pool model, because once a connection is returned to the pool, using an existing ResultSet object could give erroneous results, throw an error, or even crash the entire R process. In most cases, `DBI::dbGetQuery()` and `DBI::dbExecute()` can be used instead. If you really need the control that `dbSendQuery` gives you (for example, to process a large table in chunks) then use `poolCheckout()` to get a real connection object (and don't forget to return it to the pool using `poolReturn()` afterwards).

Usage:

```R
## S4 method for signature 'Pool'
dbSendQuery(conn, statement, ...)

## S4 method for signature 'Pool,ANY'
dbSendStatement(conn, statement, ...)

## S4 method for signature 'Pool,character'
dbGetQuery(conn, statement, ...)

## S4 method for signature 'Pool,character'
dbExecute(conn, statement, ...)

## S4 method for signature 'Pool'
dbListResults(conn, ...)

## S4 method for signature 'Pool,character'
dbListFields(conn, name, ...)

## S4 method for signature 'Pool'
dbListTables(conn, ...)

## S4 method for signature 'Pool'
dbListObjects(conn, prefix = NULL, ...)

## S4 method for signature 'Pool,character'
dbReadTable(conn, name, ...)

## S4 method for signature 'Pool,ANY'
dbWriteTable(conn, name, value, ...)

## S4 method for signature 'Pool'
dbCreateTable(conn, name, fields, ..., row.names = NULL, temporary = FALSE)

## S4 method for signature 'Pool'
dbAppendTable(conn, name, value, ..., row.names = NULL)

## S4 method for signature 'Pool,ANY'
dbExistsTable(conn, name, ...)

## S4 method for signature 'Pool,ANY'
dbRemoveTable(conn, name, ...)

## S4 method for signature 'Pool'
dbIsReadOnly(dbObj, ...)
```

Where `conn` and `dbObj` are **Pool** objects, as returned by `dbPool()`.

See DBI Documentation for remaining parameters/arguments.

### poolCreate

`poolCreate` is an **S4** class for compatibility with the `DBI` methods.

The main difference to consider here is that `poolCreate` builds off an existing `factory` function responsible for the generation of the objects that the pool will hold (ex: for DBI database connections, this function is `dbConnect`). **It must take no arguments.**

#### Example Usage

Will provide two example `factory` functions to pass to `pool::poolCreate`, one using `DBI` and the other using `dbx`:

- DBI:

```R
library(DBI)


# DBI factory function

factory_fn_dbi <- function() { # note: no args in the factory function
  DBI::dbConnect(
    Postgres(), 
    host = "<host>", 
    dbname = "<dbname>",
    user = "postgres", 
    password = "<password>", 
    port = "5432"
  )
}

pool <- poolCreate(factory = factory_fn_dbi)

pool::poolClose(pool)
```

- dbx:

```R
library(dbx)
library(RPostgres)
library(pool)

factory_fn_dbx <- function() dbx::dbxConnect(<database-URI>)

pool <- poolCreate(factory = factory_fn_dbx)

pool::poolClose(pool)
```

### dbPool

`dbPool` Creates a DBI Database Connection Pool serving as a wrapper around `poolCreate` to simplify the creation of a DBI database connection pool.

Check the documentation of `poolCreate()` for a generic overview of the parent function and the Pool object. 

The main thing to point out is that, for `dbPool`,  **you always need to provide a DBI driver** (i.e. of class DBI::DBIDriver-class()), and it should always be accompanied by the required authorization arguments (see the example below).

```R
dbPool(drv, ..., validateQuery = NULL)
```

Example:

```R
pool <- pool::dbPool(drv = RPostres::Postgres(), < database connection arguments >)
```

### The `pool` Object:

```R
pool <- poolCreate(
  factory,
  minSize = 1,
  maxSize = Inf,
  idleTimeout = 60,
  validationInterval = 600,
  state = NULL
)

factory_fn <- function() DBI::dbConnect(<connection_params>)

pool <- poolCreate(factory_fn)

> class(pool)

[1] "Pool" "R6"

> str(pool)

Classes 'Pool', 'R6' <Pool>
  Public:
    clone: function (deep = FALSE) 
    close: function () 
    counters: environment
    fetch: function () 
    idleTimeout: 60
    initialize: function (factory, minSize, maxSize, idleTimeout, validationInterval, 
    maxSize: Inf
    minSize: 1
    release: function (object) 
    state: NULL
    valid: TRUE
    validationInterval: 600
		
  Private:
    cancelScheduledTask: function (object, task) 
    changeObjectStatus: function (object, to) 
    checkValid: function (object) 
    checkValidTemplate: function (object, errorFun) 
    createObject: function () 
    destroyObject: function (object) 
    factory: function () 
    freeObjects: environment
    idCounter: 2
    validate: function (object)  
		
```

As you can see above a `pool` object in R is classified with two classes: `R6` and `Pool` which can be useful in many ways:
- To determine a connections type for reference/informational purposes
- Dispatch generic methods onto the connection objects by utilizing their inherited classes (i.e. through `if (inherits(conn, "R6"`) corresponding methods connections bases off their inherited classes. 
		- As opposed to a direct DBI connection which would inherit the class of the database driver's specifications: i.e.

```R
conn <- poolCheckout(pool)

> class(conn)

[1] "PqConnection"
attr(,"package")

[1] "RPostgres"

> str(conn)

Formal class 'PqConnection' [package "RPostgres"] with 5 slots
  ..@ ptr         :<externalptr> 
  ..@ bigint      : chr "integer64"
  ..@ timezone    : chr "UTC"
  ..@ timezone_out: chr "UTC"
  ..@ typnames    :'data.frame':	487 obs. of  2 variables:
  .. ..$ oid    : int [1:487] 16 17 18 19 20 21 22 23 24 25 ...
  .. ..$ typname: chr [1:487] "bool" "bytea" "char" "name" ...
```

Notice that by checking out the pool object using `conn <- pool::poolCheckout(pool)` the newly created `conn` connection argument now resembles the default `DBI::dbConnect(...)` returning object's attributes, classes, etc.


***
Links: 
Source:

