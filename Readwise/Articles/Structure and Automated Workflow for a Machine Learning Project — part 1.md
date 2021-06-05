%%
ID: 4212938
Updated: 2020-08-28
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

# About
Title: [[Structure and Automated Workflow for a Machine Learning Project — part 1]]
Author: [[Mateusz Bednarski]]
Category: #articles
Number of Highlights: ==7==
Last Highlighted: *2020-08-27*
Readwise URL: https://readwise.io/bookreview/4212938
Source URL: https://towardsdatascience.com/structure-and-automated-workflow-for-a-machine-learning-project-2fa30d661c1e


# Highlights 
Let’s start with creating reproducible environment. Create file called environment.yml We can start with following content:  ^81110256

**Note: environment.yml - do this: 
dependencies:
  - R=4.0.2
  - Package1=<version>
  - Package2=<version>
  - ...
  - external libs**

---

Downloading data
First step is to download the data. But we will not do it by copying from Downloads directory . Instead: we can create python script in src/data/download.py  ^81110257

---

So let’s start fixing this issues. At the beginning create directory structure for data. There would be three of them:

data/raw - here all raw data exists. This directory should be considered as read only - just leave what we got as it is.
data/processed - data after whole preprocessing, merging, cleaning, feature engineering etc.
data/interim - intermediate format between raw and processed. Not raw and also not ready yet.
data/external - any data we consider as being external. E.g dictionaries, synonyms.  ^81110258

---

Git does not store empty directories. By creating an empty .gitkeep file we can enforce directory persistence. By default, data should not be stored in git repository — so that we need to adjust .gitignore:  ^81110259

---

Workflow
OK, we solved issue with directories. Let’s move on to workflow. Downloading is very first step and should be written correctly. But what does it mean? Parameters should be possible to pass by command line arguments. For that we will use click library. Add to environment.yml  ^81110260

---

Make
Now we are ready to automate workflow. We will use … GNU Make. No. I’m not joking. This tool suits very well for our needs. Also writing Makefiles is not as scary as you might think. Interesting fact: in practice this is very portable solution between Linux, Mac and Windows.

Our first workflow will consist of three steps.

clean - will remove all generated output
all - will run whole pipeline from beginning to the end
download - will download the data  ^81110261

---

OK, so what are benefits of presented approach?

You will be able to perform whole process from grabbing the data to generate reports by one command
You will be able to reproduce your work
You will thank yourself after a year when come back to project
Others will be able to understand your code (also potential employers)  ^81110262

