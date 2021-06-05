%%
ID: 4212939
Updated: 2020-08-28
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article0.00998d930354.png)

# About
Title: [[The Data Science Workflow]]
Author: 
Category: #articles
Number of Highlights: ==29==
Last Highlighted: *2020-08-27*
Readwise URL: https://readwise.io/bookreview/4212939
Source URL: https://towardsdatascience.com/the-data-science-workflow-43859db0415


# Highlights 
Source data access  ^81110263

---

your first step is to define access to the source data.  ^81110264

---

Your source data is provided as a set of *.csv files. You follow the cookiecutter-data-science approach, make a data/raw subdirectory in your project's root folder, and put all the files there. You create the docs/data.rst file, where you describe the meaning of your source data. (Note: Cookiecutter-DataScience template actually recommends references/ as the place for data dictionaries, while I pesonally prefer docs. Not that it matters much).  ^81110265

**Note: This is python specific - I life the idea of references folder though as well as a restructured-text documentation ".rst" file although i would use markdown.**

---

Your source data is provided as a set of *.csv files. You set up an SQL server, create a schema named raw and import all your CSV files as separate tables. You create the docs/data.rst file, where you describe the meaning of your source data as well as the location and access procedures for the SQL server.  ^81110266

---

Your source data is a messy collection of genome sequence files, patient records, Excel files and Word documents, which may later grow in unpredicted ways. In addition, you know that you will need to query several external websites to receive extra information. You create an SQL database server in the cloud and import most of the tables from Excel files there. You create the data/raw directory in your project, put all the huge genome sequence files into the dna subdirectory. Some of the Excel files were too dirty to be imported into a database table, so you store them in data/raw/unprocessed directory along with the Word files. You create an Amazon S3 bucket and push your whole data/raw directory there using DVC. You create a Python package for querying the external websites. You create the docs/data.rst file, where you specify the location of the SQL server, the S3 bucket, the external websites, describe how to use DVC to download the data from S3 and the Python package to query the websites. You also describe, to the best of your understanding, the meaning and contents of all the Excel and Word files as well as the procedures to be taken when new data is added.  ^81110267

---

Your source data consists of constantly updated website logs. You set up the ELK stack and configure the website to stream all the new logs there. You create docs/data.rst, where you describe the contents of the log records as well as the information needed to access and configure the ELK stack.  ^81110268

---

Your source data is a simulated dataset. You implement the dataset generation as a Python class and document its use in a README.txt file.  ^81110269

---

In general, remember the following rules of thumb when setting up the source data:  ^81110270

---

Whenever you can meaningfully store your source data in a conveniently queryable/indexable form (an SQL database, the ELK stack, an HDF5 file or a raster database), you should do it. Even if your source data is a single csv and you are reluctant to set up a server, do yourself a favor and import it into an SQLite file, for example. If your data is nice and clean, it can be as simple as:  ^81110271

**Note: import sqlalchemy as sa
import pandas as pd
e = sa.create_engine("sqlite:///raw_data.sqlite")
pd.read_csv("raw_data.csv").to_sql("raw_data", e)**

---

If you work in a team, make sure the data is easy to share. Use an NFS partition, an S3 bucket, a Git-LFS repository, a Quilt package, etc.  ^81110272

---

Make sure your source data is always read-only and you have a backup copy.  ^81110273

---

Take your time to document the meaning of all of your data as well as its location and access procedures.  ^81110274

---

In general, take this step very seriously. Any mistake you make here, be it an invalid source file, a misunderstood feature name, or a misconfigured server may waste you a lot of time and effort down the road.  ^81110275

---

Data processing  ^81110276

---

The aim of the data processing step is to turn the source data into a “clean” form, suitable for use in the following modeling stage. This “clean” form is, in most cases, a table of features, hence the gist of “data processing” often boils down to various forms of feature engineering. The core requirements here are to ensure that the feature engineering logic is maintainable, the target datasets are reproducible and, sometimes, that the whole pipeline is traceable to the source representations (otherwise you would not be able to deploy the model). All these requirements can be satisfied, if the processing is organized in an explicitly described computation graph. There are different possibilities for implementing this graph, however. Here are some examples:  ^81110277

---

You follow the cookiecutter-data-science route and use Makefiles to describe the computation graph. Each step is implemented in a script, which takes some data file as input and produces a new data file as output, which you store in the data/interim or data/processed subdirectories of your project. You enjoy easy parallel computation via make -j <njobs>.  ^81110278

---

You rely on DVC rather than Makefiles to describe and execute the computation graph. The overall procedure is largely similar to the solution above, but you get some extra convenience features, such as easy sharing of the resulting files.  ^81110279

---

You use Luigi, Airflow or any other dedicated workflow management system instead of Makefiles to describe and execute the computation graph. Among other things this would typically let you observe the progress of your computations on a fancy web-based dashboard, integrate with a computing cluster’s job queue, or provide some other tool-specific benefits.  ^81110280

---

All of your source data is stored in an SQL database as a set of tables. You implement all of the feature extraction logic in terms of SQL views. In addition, you use SQL views to describe the samples of objects. You can then use these feature- and sample-views to create the final modeling datasets using auto-generated queries like  ^81110281

---

Firstly, it lets you keep track of all the currently defined features easily without having to store them in huge data tables — the feature definitions are only kept as code until you actually query them. Secondly, the deployment of models to production becomes rather straightforward — assuming the live database uses the same schema, you only need to copy the respective views. Moreover, you may even compile all the feature definitions into a single query along with the final model prediction computation using a sequence of CTE statements:  ^81110282

---

This technique has been implemented in one in-house data science workbench tool of my design (not publicly available so far, unfortunately) and provides a very streamlined workflow.  ^81110283

---

Example of an SQL-based feature engineering pipeline
No matter which way you choose, keep these points in mind:

Always organize the processing in the form of a computation graph and keep reproducibility in mind.
This is the place where you have to think about the compute infrastructure you may need. Do you plan to run long computations? Do you need to parallelize or rent a cluster? Would you benefit from a job queue with a management UI for tracking task execution?
If you plan to deploy the models into production later on, make sure your system will support this use case out of the box. For example, if you are developing a model to be included in a Java Android app, yet you prefer to do your data science in Python, one possibility for avoiding a lot of hassle down the road would be to express all of your data processing in a specially designed DSL rather than free-from Python. This DSL may then be translated into Java or an intermediate format like PMML.
Consider storing some metadata about your designed features or interim computations. This does not have to be complicated — you can save each feature column to a separate file, for example, or use Python function annotations to annotate each feature-generating function with a list of its outputs. If your project is long and involves several people designing features, having such a registry may end up quite useful.  ^81110284

---

Exploration and reporting
Throughout the life of the data science project you will constantly have to sidestep from the main modeling pipeline in order to explore the data, try out various hypotheses, produce charts or reports. These tasks differ from the main pipeline in two important aspects.

Firstly, most of them do not have to be reproducible. That is, you do not absolutely need to include them in the computation graph as you would with your data preprocessing and model fitting logic. You should always try to stick to reproducibility, of course — it is great when you have all the code to regenerate a given report from raw data, but there would still be many cases where this hassle is unnecessary. Sometimes making some plots manually in Jupyter and pasting them into a Powerpoint presentation serves the purpose just fine, no need to overengineer.

The second, actually problematic particularity of these “Exploration” tasks is that they tend to be somewhat disorganized and unpredictable. One day you might need to analyze a curious outlier in the performance monitoring logs. Next day you want to test a new algorithm, etc. If you do not decide on a suitable folder structure, soon your project directory will be filled with notebooks with weird names, and no one in the team would understand what is what. Over the years I have only found one more or less working solution to this problem: ordering subprojects by date. Namely:

You create a projects directory in your project folder. You agree that each "exploratory" project must create a folder named projects/YYYY-MM-DD - Subproject title, where YYYY-MM-DD is the date when the subproject was initiated. After a year of work your projects folder looks as follows:  ^81110285

---

Note that you are free to organize the internals of each subproject as you deem necessary. In particular, it may even be a “data science project” in itself, with its own raw/processed data subfolders, its own Makefile-based computation graph, as well as own subprojects (which I would tend to name tasks in this case). In any case, always document each subproject (have a README file at the very least). Sometimes it helps to also have a root projects/README.txt file, which briefly lists the meaning of each subproject directory.  ^81110286

---

Eventually you may discover that the project list becomes too long, and decide to reorganize the projects directory. You compress some of them and move to an archive folder. You regroup some related projects and move them to the tasks subdirectory of some parent project.  ^81110287

---

Exploration tasks come in two flavors. Some tasks are truly one-shot analyses, which can be solved using a Jupyter notebook that will never be executed again. Others aim to produce reusable code (not to be confused with reproducible outputs). I find it important to establish some conventions for how the reusable code should be kept. For example, the convention may be to have a file named script.py in the subproject's root which outputs an argparse-based help message when executed. Or you may decide to require providing a run function, configured as a Celery task, so it can easily be submitted to the job queue. Or it could be something else - anything is fine, as long as it is consistent.  ^81110288

---

The service checklist
There is an other, orthogonal perspective on the data science workflow, which I find useful. Namely, rather than speaking about it in terms of a pipeline of processes, we may instead discuss the key services that data science projects typically rely upon. This way you may describe your particular (or desired) setup by specifying how exactly should each of the following 9 key services be provided:  ^81110289

---

File storage. Your project must have a home. Often this home must be shared by the team. Is it a folder on a network drive? Is it a working folder of a Git repository? How do you organize its contents?
Data services. How do you store and access your data? “Data” here includes your source data, intermediate results, access to third-party datasets, metadata, models and reports — essentially everything which is read by or written by a computer. Yes, keeping a bunch of HDF5 files is also an example of a “data service”.
Versioning. Code, data, models, reports and documentation — everything should be kept under some form of version control. Git for code? Quilt for data? DVC for models? Dropbox for reports? Wiki for documentation? Once we’re at it, do not forget to set up regular back ups for everything.
Metadata and documentation. How do you document your project or subprojects? Do you maintain any machine-readable metadata about your features, scripts, datasets or models?
Interactive computing. Interactive computing is how most of the hard work is done in data science. Do you use JupyterLab, RStudio, ROOT, Octave or Matlab? Do you set up a cluster for interactive parallel computing (e.g. ipyparallel or dask)?
Job queue & scheduler. How do you run your code? Do you use a job processing queue? Do you have the capability (or the need) to schedule regular maintenance tasks?
Computation graph. How do you describe the computation graph and establish reproducibility? Makefiles? DVC? Airflow?
Experiment manager. How do you collect, view and analyze model training progress and results? ModelDB? Hyperdash? FloydHub?
Monitoring dashboard. How do you collect and track the performance of the model in production? Metabase? Tableau? PowerBI? Grafana?  ^81110290

---

The tools
To conclude and summarize the exposition, here is a small spreadsheet, listing the tools mentioned in this post (as well as some extra ones I added or will add later on), categorizing them according to which stages of the data science workflow (in the terms defined in this post) they aim to support. Disclaimer — I did try out most, but not all of them. In particular, my understanding of the capabilities of the non-free solutions in the list is so far only based on their online demos or descriptions on the site.  ^81110291

