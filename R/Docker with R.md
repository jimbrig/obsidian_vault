---
creation date: 2021-05-21 18:14
modification date: Friday 21st May 2021 18:14:36
tags: ["#R", "#dev", "#docker"]
author: Jimmy Briggs
---

# Docker with R

## Parent Docker Images

A parent image is an image that you define in the `FROM` directive of the `Dockerfile`. A [base image](https://docs.docker.com/develop/develop-images/baseimages/) has `FROM scratch` as the first line. The R base images start with parent images. For example, the R Ubuntu image starts with `FROM ubuntu:focal`.

Here are the four commonly used parent images for R:

```bash
docker pull rhub/r-minimal:4.0.5
docker pull rocker/r-base:4.0.4
docker pull rocker/r-ubuntu:20.04
docker pull rstudio/r-base:4.0.4-focal
```

The image sizes vary quite a bit with the Alpine Linux base `rhub/r-minimal` being smallest and the Ubuntu-based `rstudio/r-base` 25x the size of the smallest image:

```bash
$ docker images --format 'table {{.Repository}}\t{{.Tag}}\t{{.Size}}'

REPOSITORY          TAG                 SIZE
rhub/r-minimal      4.0.5               35.3MB
rocker/r-base       4.0.4               761MB
rocker/r-ubuntu     20.04               673MB
rstudio/r-base      4.0.4-focal         894MB
```

The Debian Linux based `rocker/r-base` Docker image from the [Rocker](https://github.com/rocker-org/rocker/tree/master/r-base) project is considered bleeding edge when it comes to system dependencies, i.e. latest development versions are usually available sooner than on other Linux distributions.

The two Ubuntu Linux based images, `rocker/r-ubuntu` and `rstudio/r-base` from the [Rocker](https://github.com/rocker-org/rocker/tree/master/r-ubuntu) project and from [RStudio](https://github.com/rstudio/r-docker) are for long-term support Ubuntu versions and use the [RSPM](https://packagemanager.rstudio.com/client/) CRAN binaries.

The Alpine Linux based `rhub/r-minimal` Docker image from the [r-hub](https://github.com/r-hub/r-minimal) project is preferred for its small image sizes.

## Using BuildKit

- [Docker BuildKit](https://docs.docker.com/develop/develop-images/build_enhancements/)

Docker versions 18.09 or higher come with a new opt-in builder backend called [BuildKit](https://github.com/moby/buildkit). BuildKit prints out a nice summary of each layer including timing for the layers and the overall build. This is the general build command that I used to compare the four parent images:

```bash
DOCKER_BUILDKIT=1 docker build --no-cache -f $FILE -t $IMAGE .
```

BuildKit backend is enabled by turning on the `DOCKER_BUILDKIT=1` environment variable. I use the `--no-cache` option to avoid using cached layers, thus having a fair assessment of build times (you usually only build 1 and not 4). The `-f $FILE` flag allows building from different files kept in the same folder.

## Gathering Elements of Computational Environment

Before the creation of a `Dockerfile`, first, one must collect and determine everything involved in re-producing the development environment. This includes, but is not limited to:

- R Package Dependencies
- R Package System Requirements
- Configurations and Environment Variables
- An Entrypoint or Execution Command to Launch the Process

### Determining R Package Dependencies

Depending on the type of project you are working on, the method in which R Package Dependencies can be extracted can vary. For example, if you are building an R Package all external dependencies will already be 
specified in the package's `DESCRIPTION` file. Alternatively, in a standalone analysis project composed of R scripts and/or R Markdown documents package dependencies will be loaded via `library`, `require`, or called directly via `::`/`:::`, etc. 

Methods of R Package Dependency Detection by Project Type:

| Project Type       | Methodology                                                                    |
| ------------------ | ------------------------------------------------------------------------------ |
| R Package          | Extract from `DESCRIPTION`                                                     |
| General R Analysis | Scrape `.R` and `.Rmd` files for any calls to `library`, `require`, `::`, etc. |
| Current Session    | Scrape `sessionInfo()`                                                         |

Some useful packages and functions to use for determining exactly what R packages your project depends on include:

- `sessionInfo()`, `sessioninfo::sessioninfo()`
- `requirements::req_code()`, `requirements::req_file()`, `requirements::req_namespace()`
- `renv::dependencies()`
- `automagic::get_dependent_packages()`, `automagic::make_deps_file()`
- `dep::get_deps()`, `dep::get_proj_deps()`
- `rsconnect::appDependencies()`

Packages:

- `containerit`
- `dockerfiler`
- `stevedore`
- `dockermachine`
- `littlr`
- `dockerstats`
- `repro`
- `automagic`
- `requirements`
- `versions`
-   `httpcache`
-   `sysreqs`
-   `golem`
-   `attachment`
-   `pak`
-   `MarkEdmonsons suite for GCP`
-   `sys`
-   `rsconnect`
-   `tic.package`
-   `rpushbullet`
-   `rockerbuilder`
-   `r-minimal`
-   `dockertest`
-   `rize`
-   `dockeRs`
-   `docker`
-   `dada2docker`
-   `repo2docker`
-   `podman-compose`
-   `vcr` (record HTTP calls and replay them)

For installation in the `Dockerfile` use the following tips:

- Consider using the `versions` package over `remotes` for better installations.
- Support package installation through a single `dependencies.R` script (`attachment::create_dependencies_file()`).
- Similarly, for system requirements, support `apt.txt` files.
- Utilize `renv`'s caching support functionality within containers (see https://www.robertmylesmcdonnell.com/content/posts/docker/)
- Add metadata in `Dockerfile` such as:
	- Maintainer - `whoami::whoami()$fullname()`
	-   Build Date - `Sys.Date()`
	-   Labels
	-   App Version with automatic incrementing `semver`
	-   Remote Repository Specs
- Utilize a `.dockerignore` file
- Option to build image/deploy app as an RStudio background job via `rstudioapi::runJob()`
- Add logging


## System Requirements

- `dep::get_sysreqs()`

***
Links: [[R Development]] | [[Docker]] | [[Shiny Apps as Packages in R]]
Source:

