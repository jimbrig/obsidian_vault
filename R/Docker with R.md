---
creation date: 2021-05-21 18:14
modification date: Friday 21st May 2021 18:14:36
tags: ["#R", "#dev", "#docker"]
author: Jimmy Briggs
---

# Docker with R

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

For installation in the `Dockerfile` use the following tips:

- Consider using the `versions` package over `remotes` for better installations.
- Support package installation through a single `dependencies.R` script (`attachment::create_dependencies_file()`).
- Similarly, for system requirements, support `apt.txt` files.
- Utilize `renv`'s cach'

## System Requirements

- `dep::get_sysreqs()`

***
Links: [[R Development]] | [[Docker]] | [[Shiny Apps as Packages in R]]
Source:

