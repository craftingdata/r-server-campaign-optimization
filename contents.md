---
layout: default
title: Template Contents
---

## Template Contents
--------------------

The following is the directory structure for this template:

- [**Data**](#copy-of-input-datasets)  This contains the copy of the simulated input data
- [**R**](#model-development-in-r)  This contains the R codes to simulate the input datasets, create the analytical datasets, train the models, identify champion model and score the analytical/scorings dataset
- [**Resources**](#resources-for-the-solution-packet) This directory contains other resources for the solution packet
- [**SQLR**](#operationalize-in-sql-2016) This contains the SQLR codes to simulate the input datasets, create the analytical datasets, train the models, identify champion model and score the analytical/scorings dataset. It also contains PowerShell scripts automate the entire process

In this template with SQL Server R Services, two versions of the implementation:

1. [**Model Development in R IDE**](#model-development-in-r)  . Run the R code in R IDE (e.g., RStudio, R Tools for Visual Studio).
2. [**Operationalize in SQL**](#operationalize-in-sql-2016). Run the SQL code in SQL Server using SQLR scripts, automated with the use of a PowerShell script.


### Copy of Input Datasets
----------------------------

<table class="table table-striped table-condensed">
<tr><th> File </th><th> Description</th></tr>
<tr><td> .\Data\Campaign_Detail.csv </td><td> Campaign Metadata </td></tr>
<tr><td> .\Data\Market_Touchdown.csv </td><td>  Historical Campaign data including lead responses </td></tr>
<tr><td> .\Data\Product.csv </td><td>  Product Metadata </td></tr>
<tr><td> .\Data\Lead_Demography.csv </td><td>  Demographic data of the leads </td></tr>
</table>

### Model Development in R
-------------------------

<table class="table table-striped table-condensed">
<tr><th> File </th><th> Description </th></tr>
<tr><td>SQL_connection.R </td><td> Contains details of connection to SQL Server used in all other scripts </td></tr>
<tr><td>step0_data_generation.R </td><td> Simulates the 4 input datasets, not needed unless you wish to regenerate data </td></tr>
<tr><td> step1_data_processing.R </td><td> uploads .csv files to SQL and performs data preprocessing steps such as outlier treatment and missing value treatment  </td></tr>
<tr><td>step2_feature_engineering.R </td><td> Performs Feature Engineering and creates the Analytical Dataset </td></tr>
<tr><td>step3_training_evaluation.R </td><td> Builds the Random Forest &amp; Gradient Boosting models, identifies the champion model </td></tr>
<tr><td>step4_campaign_recommendations.R </td><td>Build final recommendations from scoring 63 combinations per lead and selecting combo with highest conversion probability  </td></tr>
</table>


* See the [Typical Workflow](Typical.html) documentation to execute these scripts.


### Operationalize in SQL 2016 
-------------------------------------------------------

<table class="table table-striped table-condensed">
<tr><th> File </th><th> Description </th></tr>
<tr><td> .\SQLR\step0_create\tables.sql </td><td> SQL Script to upload data tables into SQL </td></tr>
<tr><td> .\SQLR\step1_data_processing.sql  </td><td> Missing values in data tables are treated </td></tr>
<tr><td> .\SQLR\step2_feature_engineering.sql </td><td> Performs Feature Engineering and creates the Analytical Dataset</td></tr>
<tr><td> .\SQLR\step43a_splitting.sql </td><td> Split the analytical dataset (AD) into Train and Test</td></tr>
<tr><td> .\SQLR\Step3b_train_model.sql</td><td> Trains either RF or GBT model, depending on input parameter</td></tr>
<tr><td> .\SQLR\Step3c_test_model.sql </td><td> Tests both RF and GBT model</td></tr>
<tr><td> .\SQLR\step4_campaign_recommendations.sql </td><td> Scores data with best model and outputs recommendations </td></tr>
<tr><td>.\SQLR\Campaign_Optimization.ps1 </td><td> Load the input data into the SQL server and automates the running of all .sql files  </td></tr>
</table>


* Follow the [PowerShell Instructions](Powershell_Instructions.html) to execute the PowerShell script which automates the running of all these .sql files.





### Resources for the Solution Packet
------------------------------------

<table class="table table-striped table-condensed">
<tr><th> File </th><th> Description </th></tr>

<tr><td> .\Resources\createuser.sql </td><td> Used during initial SQL Server setup </td></tr>
<tr><td> .\Resources\Images\ </td><td> Directory of images used for the  Readme.md  in this package </td></tr>
</table>




[&lt; Home](index.html)