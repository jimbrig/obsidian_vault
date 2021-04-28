---
creation date: 2021-04-28 10:25
modification date: Wednesday 28th April 2021 10:25:18
tags: ["#r"]
author: Jimmy Briggs
---

# R Miscellaneous Notes

\### Package Development Guidelines

The  script should be used to document all changes and additions to
package code. In addition, git-flow branches should be used for all
added features and bug fixes. The \*\*development\*\* branch serves as the
“test” / “work-in-progress” branch while the \*\*master\*\* branch is the
“production” branch and should only be updated when creating a new
\*\*release\*\*.

For example, say I wanted to add a new feature / function - the
following steps would be used:

1.  Using \*Git-Flow\*, a new branch should be created off the current
    \*\*development\*\* branch with a name corresponding to the new feature.
2.  Once in the new branch, add functions via the \*\*devhist.R\*\* script
    via .
3.  Edit the new .R file and commit changes and push to feature branch.
4.  Add tests for new function and document additions via , and document
    this in the \*\*devhist.R\*\* script.
5.  Add example usage of the new feature via , and document this in the
    \*\*devhist.R\*\* script.
6.  Document, Test, Check, Build, and Install.
7.  Finally, merge feature branch with development branch using git-flow
    and if desired create a new release and merge with master branch
    updating the package version.
	
	### Ideas
	
	### Functions

#### Workflow Functions

  - Project Configuration
  - Version Control and Git
  - Directory Structure
  - Project Variables
  - External Data Sources
  - Caching
  - Pipelines
  - Databases and Query’s
  - GoogleDrive
  - Files Metadata
  - Codebooks, Data Dictionaries, Name Tables
  - Documentation
  - CI
  - Testing
  - Code Review

#### Actuarial Functions

  - Compare to Prior
  - Retentions
  - Policy Periods
  - Grouping by Occurrence
  - Exposure Lagging
  - Experience Mod Factors
  - Industry Loss Costs
  - Data Validation Checks
  - Manual Adjustments
  - Triangle Formation
  - LDF Derivation
  - LDF Interpolation
  - Discount Factors
  - Data Summaries
  - Loss Costs
  - Severity
  - Frequency
  - Credibiilty
  - Allocation
  - Projections
  - Development Methods
  - BF Methods
  - Parrallelogram Methods
  - Evaluation Dates / Year-Month Time Series Data
  - Persistency
  - NCCI
  - Credibility
  - Simulations and Confidence Intervals / Levels
  - Benchmarking
  - Contigency Tables
  - Survival Analysis

#### Utility Functions

  - Parsing
  - Dates
  - Excel

### Data Structures

  - Lossruns
  - Triangles
  - Exposures
  - Industry Loss Costs

### RStudio Addins

  - Project Init
  - Dependencies
  - Styling
  - Create Script with Header
  - Git Setup
  - Name Table Addin
  - Excel Integration Addin(s)
  - Remote / Raw Data Directories (Persistent Data Storage)
  - Shiny App Init
  - Find and Replace
  - Data Manipulation (MiniUI with a Pivot Table)
  - Markdown Addins
  - Prefixer / @importFrom
  - Clipboard

### Templates

  - Project Directory
  - Package Directory
  - Shiny App Directory
  - Markdown HTML Template
  - README Template
  - Package DESCRIPTION template
  - Excel Output Template
  - Shiny Apps HTML Templates
  - HTML Widget Templates
  - PDF Acturial Report Template
  - Latex Tables

### Shiny Apps

  - Modules
  - Highcharter
  - DT
  - CSS, Bootstrap, Java, HTML

### Options

  - Global options
  - .Rprofile
  - .Renviron
  - Git
  - BB & GH
  - Conflicts
  - DT
  - Knitr
  - Pre-Commit Hooks
  - Shiny
  - Highcharter

### Data

  - CRM - People, Emails, Phones, Expertise, Clients, Budgets, etc.
  - Historical Archived Data (Versioning)
  - Git LFS
  - Example Lossruns, Exposures, Industry Data
  - Triangles, LDFs, Discount Factors
  - Simulation Outputs
  - Transactional Data
  - Liberty, Sedgwick, etc extraction.

### Resources and Learning

  - <https://rtask.thinkr.fr/when-development-starts-with-documentation/>
  - <https://emilyriederer.netlify.com/post/rmarkdown-driven-development/>
  - <https://r-pkgs.org/index.html>
  - <https://github.com/ThinkR-open/golem>
  - <https://thinkr-open.github.io/building-shiny-apps-workflow/>
  - <https://github.com/ThinkR-open/chameleon>
  - <https://github.com/rorynolan/exampletestr>
  - <https://github.com/ThinkR-open/attachment/blob/master/devstuff\_history.R>

***
Links: 
Source:

