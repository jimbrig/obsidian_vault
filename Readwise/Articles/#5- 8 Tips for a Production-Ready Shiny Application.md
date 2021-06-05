%%
ID: 6517860
Updated: 2020-12-02
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[#5- 8 Tips for a Production-Ready Shiny Application]]
Author: [[rinproduction.com]]
Category: #articles
Number of Highlights: ==9==
Last Highlighted: *2020-12-02*
Readwise URL: https://readwise.io/bookreview/6517860
Source URL: https://www.rinproduction.com/en/posts/005-8-tips-for-a-production-ready-shiny-application/


# Highlights 
This brings up the first challenge: managing the increasing complexity of the application. The solution is obtained with a strategy of divide and conquer, that is to divide a complex system into smaller parts, and consequently, more understandable and more manageable. The criterion with which to carry out the division is the separation of competences: which we can exemplify in the division into components or in the coding of elementary objects to be used throughout the interface to give consintency of treatment to similar parts  ^116034852

---

On the other hand, the elementary objects can be, for example, a particular type of table, or graph, or widget that is used by the whole application in order to make it consistent with itself.  ^116034853

---

A first level of separation of competences is the division of the application into Shiny modules. The latter can be said to be miniature Shiny applications, because they are characterized by a front-end (User Interface) part and from a back-end one (Server) which contains reactive objects  ^116034854

---

Separate Shiny and Simple R code into different filesThe second level of separation of competences splits the Shiny part, from the simple R code. This practice is very important and separates the update logic (reactive) contained in the Shiny module, from the calculation logic that lives in R functions, which can be used separately from the reactive context (reactive context), allowing it to be used and tested independently.  ^116034855

---

Shiny is given to us with great freedom of organization. Just create a directory with some files with standard names and the rest we can decide at will: create a data folder, a folder for the base R code, etc&mldr; However these freedoms imply the obligation to create, according to the choices made, a number of procedures to perform tasks that are actually very common. For example, how do I organize the project folder? How do I define code dependencies and make sure they are installed on the system? Actually these tasks already have an absolutely standard solution encoded in the idea of R Package. In fact, creating a package means having:the form of the standard project folderthe standard documentation format for: individual functions and vignettesthe declaration of dependencies (and their versions) not only in the package name, but also at a lower level by choosing the individual functions to import.a standard and robust installation procedure starting from a wide variety of formats (tar.gz or zip files, Git repository, package on the CRAN, etc &mldr;)other standard procedures for example: testing (which I will talk about later), and sample dataset provision.  ^116034856

---

As the size and complexity of the application increases, the number of possible breaking points increases.There may be situations in which implementing a new functionality breaks an existing one. Especially in a team, I can break the features developed by colleagues, precisely because I am less aware of the details of their functioning and, as a result, the new bug can escape my control and arrive in production. So let’s talk about functionality regression. Roughly speaking, by publishing a new feature, without realizing it, we lose other features that were instead taken for granted. This situation is even more serious than the one where the new functionality is not implemented perfectly, as the regression takes away a service that is now taken for granted.  ^116034857

---

In order to do this, it is useful to set up a strategy of automatic unit tests: in this way the tests become part of the code base and everyone can test everything with one-click in seconds. This prevents regression and gives peace of mind on release.The tests provide other advantages: testing the single component allows you to reduce the bug search zone in case of failure and the test itself is a working documentation of the single unit.  ^116034858

---

Reproducibility and configurationBoth during development and when it is in production, the application must run on different systems: your colleague’s computer or the production server.For this it is important that the application is reproducible. It means it has to work on different systems. For this, at least two conditions are important: that the compatible environment is installed and that the application is configured in order to find the external resources it needs on the system it is running on.  ^116034859

---

Track used dependencies and reproduce environment (with “renv”)For the reproducibility condition, I recommend using “renv” or Docker. The first is a package that creates a Virtual environment: namely it is able to track the version of the packages used and reproduce it on another server. While the second virtualizes the whole application including, in addition to the R packets, also the file system of the operating system and the network interface. But it is certainly a more complex choice.  ^116034860

