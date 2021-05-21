---
creation date: 2021-05-21 18:28
modification date: Friday 21st May 2021 18:28:54
tags: ["#R", "#dev"]
author: Jimmy Briggs
---

# R Optimizing Package Installations

## Example Files:

### `.Rprofile`

```r
local({
  # load pipe from magrittr
  `%>%` <- magrittr::`%>%`
})

# Set Global CRAN Mirror
options(repos = c(CRAN = 'https://cloud.r-project.org'))

# install packages in parallel via 'Ncpus' argument
options(Ncpus = 6L)

# Remove Scientific Notation
options(scipen = 999)

# Set max print
options(max.print = 100)

# Update R Prompt
if (interactive()) invisible(installr::check.for.updates.R(GUI = FALSE))

# error tracing
if ('rlang' %in% loadedNamespaces()) options(error = rlang::entrace)

# turn on completion of installed package names
utils::rc.settings(ipck = TRUE)

# usethis / devtools
options(
  usethis.full_name = "Jimmy Briggs",
  usethis.protocol = "ssh",
  usethis.description = list(
    `Authors@R` = 'person(
      "Jimmy", "Briggs",
      email = "jimbrig2011@outlook.com",
      role = c("aut", "cre"),
      comment = c(ORCID = "0000-0002-7489-8787"
    ))',
    License = "MIT + file LICENSE",
    Language =  "en-US"
  )
)

# clear env
rm(list = ls())

# cleanup
# detach all attached
suppressWarnings(
  invisible(
    lapply(
      paste("package:", names(sessionInfo()$otherPkgs), sep = ""),
      detach,
      character.only = TRUE,
      unload = TRUE
      )
    )
)

# garbage collection
gc()

```

### `Makeconf` and `Makevars`

- `Makeconf`

```make
CC="ccache gcc"
CXX="ccache g++"
```

- `Makevars`

```make
VER=
CCACHE=ccache
CC=$(CCACHE) gcc$(VER)
CXX=$(CCACHE) g++$(VER)
CXX11=$(CCACHE) g++$(VER)
CXX14=$(CCACHE) g++$(VER)
FC=$(CCACHE) gfortran$(VER)
F77=$(CCACHE) gfortran$(VER)
```

## Benchmarking R Script

```r
# set default CRAN mirror for both installations
options(repos = c("CRAN" = "https://cran.rstudio.com/"))

# ensure no Ncpus already set
options(Ncpus = NULL)
is.null(getOption("Ncpus"))

# declare separate .libPaths
libpath_root <- dirname(.libPaths()[1])

# create new test libPaths for each test
lib1 <- fs::path(libpath_root, "test1")
lib2 <- file.path(libpath_root, "test2")
lib4 <- file.path(libpath_root, "test4")
lib6 <- file.path(libpath_root, "test6")

if (fs::dir_exists(lib1)) fs::dir_delete(lib1)
if (fs::dir_exists(lib2)) fs::dir_delete(lib2)
if (fs::dir_exists(lib4)) fs::dir_delete(lib4)
if (fs::dir_exists(lib6)) fs::dir_delete(lib6)

fs::dir_create(lib1, recurse = TRUE)
fs::dir_create(lib2, recurse = TRUE)
fs::dir_create(lib4, recurse = TRUE)
fs::dir_create(lib6, recurse = TRUE)

options(Ncpus = 1)
.libPaths(lib1)
start <- Sys.time(); install.packages("tidyverse", silent = TRUE); end <- Sys.time()

elapsed1 <- (end - start)
elapsed1


options(Ncpus = 2)
.libPaths(lib2)
start <- Sys.time()
install2 <- system.time(install.packages("tidyverse"))
end <- Sys.time()
elapsed2 <- (end - start)
elapsed2

options(Ncpus = 4)
.libPaths(lib4)
start <- Sys.time()
install4 <- system.time(install.packages("tidyverse"))
end <- Sys.time()
elapsed4 <- (end - start)
elapsed4


options(Ncpus = 6)
.libPaths(lib6)
start <- Sys.time()
install6 <- system.time(install.packages("tidyverse"))
end <- Sys.time()
elapsed6 <- (end - start)
elapsed6
```

- [Example copy of my R Profile](https://github.com/Tychobra/jimbrig/blob/master/docs/optimizing_package_installation/.Rprofile)
- [Example copy of my R Makeconf](./Makeconf)
- [Example copy of my R Makevars](./Makevars)
- [Script used to benchmark installation times](./installation_benchmarking_script.R)
- [Code in R Markdown Format](./package_installation_optimization.Rmd)
- [Markdown Documentation](./package_installation_optimization.md)

***

# R Package Installation Optimization


## Big Picture

Package installation time for R Packages is increasing, in general, for a number of reasons:

- Packages are getting larger and more complex (tidyverse) as well as integrating more outside development integration
- Developers are using more DevOps pipelines and CI services and want quick feedback


## Optimizing via `Ncpus`

If you are not familiar with the `Ncpus` argument to the `install.packages`/`update.packages` functions, it is a great place to start. 

From the help page for `install.packages` or `?install.packages`:

> "Ncpus: The number of parallel processes to use for a parallel install of more than one source package."

The argument allows you to install packages in parallel by allowing the user to declare the number of CPUs used in the installation command. While it does not increase the speed for individual package installations or updates, it does increase the speed that dependencies are installed through parallel installations. 

The default is 1 core (i.e. `Ncpus = getOption("Ncpus", 1L)` is the argument default). By investigating this default we can determine that you can set an option, named `Ncpus` to override the default fallback value of `1L` when no option is found. 

You can detect the number of cores on your machine through the following methods: 

- `Sys.getenv("NUMBER_OF_PROCESSORS")` will display the systems environment variable assigned to display the number of available processors.

- `parallel` package's `parallel::detectCores()` function.
  + Note there are two arguments for `all.tests` (default = `FALSE`, and `logical` (default = TRUE)) - see `?paralell::detectCores` for details.

- `ps` package's `ps::ps_cpu_count()` function.
  + Note has one argument for `logical` defaulting to `TRUE`. See `?ps::ps_cpu_count` for details.

Here's my results from the various methods:

```R
# System Environment Variable
Sys.getenv("NUMBER_OF_PROCESSORS")
[1] "12"

# Parallel Package's detectCores

# Default arguments
parallel::detectCores()
[1] 12

# All Tests FALSE
parallel::detectCores(FALSE)
[1] 12

# All Tests TRUE; Logical FALSE:
parallel::detectCores(TRUE, FALSE)
[1] 6

# PS Package's ps_cpu_count
ps::ps_cpu_count()
[1] 12
```

When setting `logical` to `FALSE` (the second argument), we get 6 cores vs 12 initially. The difference is due to the difference between physical and logical cores. On windows this can be diagnosed using the [Task Manager]():




From my output above I can determine that my Windows machine has 4 total cores, but two of these cores are due to [hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading).

Therefore, I will set a conservative value of 2 as my default `Ncpus` option in my `.Rprofile` by including this code:

```R
# in .Rprofile (i.e. "~/.Rprofile" by default)
options("Ncpus" = 2)
```

### Testing Ncpus Installation Speed

To use this argument simply call it with `install.packages()`:

```R
# install tidyverse normally
install.packages("tidyverse")

# declare six cores
install.packages("tidyverse", Ncpus = 6)
```

Let's test installation speed for tidyverse with 1 core versus 2 cores:

```R
# install tidyverse normally
install.packages("tidyverse", )

# install with 2 cores
install.packages("tidyverse", Ncpus = 2)
```

## ccache

Website: <https://ccache.dev/> 
Download: <https://ccache.dev/download.html>

Install:

```powershell
cinst csearch -y
cd ~
"" | Out-File "ccache.conf"
notepad "ccache.conf"
```

### Configure `ccache.conf`

Paste into `ccache.conf`:

```Text
max_size = 5.0G
# important for R CMD INSTALL *.tar.gz as tarballs are expanded freshly -> fresh ctime
sloppiness = include_file_ctime
# also important as the (temp.) directory name will differ
hash_dir = false
```

### Configure `~/.R/Makevars`

Set `~/.R/Makevars`:

```R
if (!dir.exists("~/.R)") dir.create("~/.R")
file.edit("~/.R/Makevars")
```

Paste into Makevars:

```Text
VER=
CCACHE=ccache
CC=$(CCACHE) gcc$(VER)
CXX=$(CCACHE) g++$(VER)
CXX11=$(CCACHE) g++$(VER)
CXX14=$(CCACHE) g++$(VER)
FC=$(CCACHE) gfortran$(VER)
F77=$(CCACHE) gfortran$(VER)
```

### Configure `~/.R/Makeconf`

Set: `~/.R/Makeconf`:

```R
if (!dir.exists("~/.R)") dir.create("~/.R")
file.edit("~/.R/Makeconf")
```

Paste into Makeconf:

```Text
CC="ccache gcc"
CXX="ccache g++"
```

## Continuous Integration Configuration

There are two important parts. First, you need to tell Travis to install `ccache` and cache its directory:

```yaml
cache:
  - $HOME/.ccache

addons:
  apt:
    packages:
     - ccache
```

Second, you need to create the required `~/.R/Makevars` file with the contents specified in Dirks post:

```yaml
before_install:
  - mkdir $HOME/.R && echo -e 'CXX_STD = CXX14\n\nVER=\nCCACHE=ccache\nCC=$(CCACHE) gcc$(VER) -std=gnu99\nCXX=$(CCACHE) g++$(VER)\nC11=$(CCACHE) g++$(VER)\nC14=$(CCACHE) g++$(VER)\nFC=$(CCACHE) gfortran$(VER)\nF77=$(CCACHE) gfortran$(VER)' > $HOME/.R/Makevars
```

According to Dirk’s post, you should also make some change to `~/.ccache/ccache.conf`. 

To do so, also add the following call to the `before_install` stage as shown above.

```yaml
- echo -e 'max_size = 5.0G\nsloppiness = include_file_ctime\nhash_dir=false' > $HOME/.ccache/ccache.conf
```

In total:

```yaml
cache:
  - $HOME/.ccache
addons:
  apt:
    packages:
     - ccache
before_install:
  - mkdir $HOME/.R && echo -e 'CXX_STD = CXX14\n\nVER=\nCCACHE=ccache\nCC=$(CCACHE) gcc$(VER) -std=gnu99\nCXX=$(CCACHE) g++$(VER)\nC11=$(CCACHE) g++$(VER)\nC14=$(CCACHE) g++$(VER)\nFC=$(CCACHE) gfortran$(VER)\nF77=$(CCACHE) gfortran$(VER)' > $HOME/.R/Makevars
  - echo -e 'max_size = 5.0G\nsloppiness = include_file_ctime\nhash_dir=false' > $HOME/.ccache/ccache.conf
```

## Benchmarking

**Benchmark Comparison Table - Tidyverse Only**

| ccache? | Cores | User | System | Elapsed |
| :-----: | :---: | :--: | :----: | :-----: |
|   NO    |   1   | 2.23 |  0.56  |  3.37   |
|   NO    |   2   | 1.79 |  0.03  |  2.07   |
|   NO    |   4   | 1.83 |  0.03  |  2.02   |
|   NO    |   6   | 1.84 |  0.06  |  2.06   |
|   YES   |   1   | 2.23 |  0.57  |  3.37   |
|   YES   |   2   | 1.78 |  0.05  |  2.01   |
|   YES   |   4   | 1.71 |  0.05  |  1.96   |
|   YES   |   6   | 1.76 |  0.06  |  2.03   |

**Benchmark Comparison Table -Fresh Installation with Dependencies**

1 Cores:  104.3955 secs / 1.739925 mins  
2 Cores:  95.36658 secs / 1.589443 mins  
4 Cores:  91.12752 secs / 1.518792 mins  
6 Cores:  90.01452 secs / 1.500242 mins  

### Results

*Using `ccache` with 6 cores produced fastest overall elapsed time, but 4 cores showed significant improvement compared to 2 (and 2 compared to 1).*

## 🔗 Links:

- <https://www.jumpingrivers.com/blog/faster-r-package-installation-rstudio/>
- <http://dirk.eddelbuettel.com/blog/2017/11/27/>
- <https://www.jumpingrivers.com/blog/speeding-up-package-installation/>
- <http://dirk.eddelbuettel.com/blog/2017/08/20/#010_stripping_shared_libraries>
- <https://en.wikipedia.org/wiki/Hyper-threading>
- <https://github.com/travis-ci/travis-build/blob/master/lib/travis/build/script/r.rb>
- <https://github.com/ropensci/tic>
- <https://ccache.dev/>
- <https://pat-s.me/post/using-ccache-to-speed-up-r-package-checks-on-travis-ci/>
- <https://stackoverflow.com/questions/36725027/r-package-installation-from-source-using-multiple-cores>
- <https://github.com/ArduPilot/ardupilot/blob/master/Tools/environment_install/install-prereqs-windows.ps1>

## Code:

```R
# set default CRAN mirror for both installations
options(repos = c("CRAN" = "https://cran.rstudio.com/"))

# ensure no Ncpus already set
options(Ncpus = NULL)
is.null(getOption("Ncpus"))

# declare separate .libPaths
libpath_root <- dirname(.libPaths()[1])

# create new test libPaths for each test
lib1 <- fs::path(libpath_root, "test1")
lib2 <- file.path(libpath_root, "test2")
lib4 <- file.path(libpath_root, "test4")
lib6 <- file.path(libpath_root, "test6")

if (fs::dir_exists(lib1)) fs::dir_delete(lib1)
if (fs::dir_exists(lib2)) fs::dir_delete(lib2)
if (fs::dir_exists(lib4)) fs::dir_delete(lib4)
if (fs::dir_exists(lib6)) fs::dir_delete(lib6)

fs::dir_create(lib1, recurse = TRUE)
fs::dir_create(lib2, recurse = TRUE)
fs::dir_create(lib4, recurse = TRUE)
fs::dir_create(lib6, recurse = TRUE)

options(Ncpus = 1)
.libPaths(lib1)
start <- Sys.time()
install.packages("tidyverse", silent = TRUE)
end <- Sys.time()
elapsed1 <- (end - start)
elapsed1


options(Ncpus = 2)
.libPaths(lib2)
start <- Sys.time()
install.packages("tidyverse", silent = TRUE)
end <- Sys.time()
elapsed2 <- (end - start)
elapsed2

options(Ncpus = 4)
.libPaths(lib4)
start <- Sys.time()
install.packages("tidyverse", silent = TRUE)
end <- Sys.time()
elapsed4 <- (end - start)
elapsed4


options(Ncpus = 6)
.libPaths(lib6)
start <- Sys.time()
install.packages("tidyverse", silent = TRUE)
end <- Sys.time()
elapsed6 <- (end - start)
elapsed6

# results in total elapsed time:
elapsed1
elapsed2
elapsed4
elapsed6
```

### Session Info

```R
> sessionInfo()
R version 4.0.3 (2020-10-10)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 10 x64 (build 20262)

Matrix products: default

locale:
[1] LC_COLLATE=English_United States.1252 
[2] LC_CTYPE=English_United States.1252   
[3] LC_MONETARY=English_United States.1252
[4] LC_NUMERIC=C                          
[5] LC_TIME=English_United States.1252    

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

loaded via a namespace (and not attached):
 [1] Rcpp_1.0.5        pillar_1.4.7      compiler_4.0.3   
 [4] installr_0.22.0   later_1.1.0.1     remotes_2.2.0    
 [7] tools_4.0.3       testthat_3.0.0    digest_0.6.27    
[10] pkgload_1.1.0     evaluate_0.14     lifecycle_0.2.0  
[13] tibble_3.0.4      jsonlite_1.7.1    pkgconfig_2.0.3  
[16] rlang_0.4.8       shiny_1.5.0       cli_2.1.0        
[19] rstudioapi_0.13   yaml_2.2.1        golem_0.2.1      
[22] xfun_0.19         fastmap_1.0.1     withr_2.3.0      
[25] stringr_1.4.0     roxygen2_7.1.1    knitr_1.30       
[28] xml2_1.3.2        vctrs_0.3.5       desc_1.2.0       
[31] fs_1.5.0          attempt_0.3.1     rprojroot_2.0.2  
[34] glue_1.4.2        R6_2.5.0          fansi_0.4.1      
[37] rmarkdown_2.5     purrr_0.3.4       dockerfiler_0.1.3
[40] magrittr_2.0.1    ellipsis_0.3.1    promises_1.1.1   
[43] htmltools_0.5.0   usethis_1.6.3     assertthat_0.2.1 
[46] mime_0.9          xtable_1.8-4      httpuv_1.5.4     
[49] config_0.3        stringi_1.5.3     crayon_1.3.4 
```


***
Links: [[R Development]]

Reference:
-   [https://www.jumpingrivers.com/blog/speeding-up-package-installation/](https://www.jumpingrivers.com/blog/speeding-up-package-installation/)
-   [http://dirk.eddelbuettel.com/blog/2017/08/20/#010\_stripping\_shared\_libraries](http://dirk.eddelbuettel.com/blog/2017/08/20/#010_stripping_shared_libraries)
-   [https://en.wikipedia.org/wiki/Hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading)
-   [https://ccache.dev/](https://ccache.dev/)
-   [https://pat-s.me/post/using-ccache-to-speed-up-r-package-checks-on-travis-ci/](https://pat-s.me/post/using-ccache-to-speed-up-r-package-checks-on-travis-ci/)
-   [https://stackoverflow.com/questions/36725027/r-package-installation-from-source-using-multiple-cores](https://stackoverflow.com/questions/36725027/r-package-installation-from-source-using-multiple-cores)
-   [https://github.com/ArduPilot/ardupilot/blob/master/Tools/environment\_install/install-prereqs-windows.ps1](https://github.com/ArduPilot/ardupilot/blob/master/Tools/environment_install/install-prereqs-windows.ps1) 

Source: <https://github.com/Tychobra/jimbrig/tree/master/docs/optimizing_package_installation>

