%%
ID: 5972288
Updated: 2020-10-23
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

# About
Title: [[Using Redo to Manage R Data Analysis Workflow]]
Author: [[karolis.koncevicius.lt]]
Category: #articles
Number of Highlights: ==6==
Last Highlighted: *2020-10-22*
Readwise URL: https://readwise.io/bookreview/5972288
Source URL: http://karolis.koncevicius.lt/posts/using_redo_to_manage_r_data_analysis_workflow/


# Highlights 
Real world data analysis projects are often complicated. They can involve multi-gigabyte input files, complex data cleaning procedures, week-long computations, and elaborate reports. Making changes and then tracking down the parts that need to be recomputed becomes close to impossible. In this article I describe my approach for dealing with this problem, which is based on a lesser known build automation tool - redo  ^103016568

**Note: “Rebuilding target files when source files have changed” on D. J. Bernstein's homepage**

---

Redo  ^103016569

---

Data science projects typically have complex pipelines involving input files, code, results, and reports. Analyses can be computationally intensive and take hours if not days or weeks to complete. Hence, data science practitioners need to be able to make changes without restarting the whole pipeline from scratch. Workflow management becomes essential and many projects turn to build automation tools like Make  ^103016570

---

Redo is a recursive build automation system that promises to be simpler and more powerful than Make. Unlike Make or its derivatives redo is tiny, recursive, and has no special syntax of its own. It allows declaring dependencies straight from within the code being executed, which enables writing scripts that “know” they will need to rerun themselves whenever their input data changes all without maintaining a separate dependency configuration file.  ^103016571

---

Standard redo workflow has several '.do' files that hold the instructions for producing every output file saved during the analysis. Computation of each target is requested with a 'redo' command which is called straight from the command line.  ^103016572

---

Some explanation is necessary. The redo command simply takes an argument and tries to produce a file of the same name. In this case the argument was 'rawdata.rds' and, given the command, redo starts looking for instructions about how to produce it. The rule for storing instructions is quite simple - they are stored in a separate file with a name constructed by adding a '.do' suffix to the original argument. In other words - redo looks for instructions about producing 'rawdata.rds' file in a file named 'rawdata.rds.do'.  ^103016573

