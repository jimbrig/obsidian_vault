%%
ID: 2977384
Updated: 2020-06-09
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[RopenscilabsDataspice- Create Lightweight schema.org Descriptions of Datas]]
Author: 
Category: #articles
Number of Highlights: ==8==
Last Highlighted: *2020-05-30*
Readwise URL: https://readwise.io/bookreview/2977384
Source URL: https://github.com/ropenscilabs/dataspice


# Highlights 
The goal of dataspice is to make it easier for researchers to create basic, lightweight, and concise metadata files for their datasets by editing the kind of files they’re probably most familiar with: CSVs. These metadata files can then be used to:

Make useful information available during analysis.
Create a helpful dataset README webpage for your data similar to how pkgdown creates websites for R packages.
Produce more complex metadata formats for richer description of your datasets and to aid dataset discovery.  ^64676876

---

Workflow
create_spice()
# Then fill in template CSV files
write_spice()
build_site() # Optional  ^64676877

---

Create spice
create_spice() creates template metadata spreadsheets in a folder (by default created in the data folder in the current working directory).

The template files are:

biblio.csv - for title, abstract, spatial and temporal coverage, etc.
creators.csv - for data authors
attributes.csv - explains each of the variables in the dataset
access.csv - for files, file types, and download URLs (if appropriate)  ^64676879

---

Fill in templates
The user needs to fill in the details of the four template files. These csv files can be directly modified, or they can be edited using either the associated helper function and/or Shiny app.

Helper functions
prep_attributes() populates the fileName and variableName columns of the attributes.csv file using the header row of the data files.

prep_access() populates the fileName, name and encodingFormat columns of the access.csv file from the files in the folder containing the data.  ^64676881

---

This function assumes that the metadata templates are in a folder called metadata within a data folder.  ^64676882

---

Using purrr::map(), this function can be applied over multiple files to populate the header names

data_files %>%
  purrr::map(~ prep_attributes(.x, attributes_path),
             attributes_path = attributes_path)  ^64676883

---

Build website
build_site() creates a bare-bones index.html file in the repository docs folder with a simple view of the dataset with the metadata and an interactive map. For example, this repository results in this website  ^64676884

---

Contributors
This package was developed at rOpenSci’s 2018 unconf by (in alphabetical order):

Carl Boettiger
Scott Chamberlain
Auriel Fournier
Kelly Hondula
Anna Krystalli
Bryce Mecum
Maëlle Salmon
Kate Webbink
Kara Woo  ^64676885

