## ANT305: Data science and DataOps workflows with Amazon EMR Studio
Venetian: Level 2, Titian 2305

Have you ever felt that building data science applications, data engineering pipelines, or machine learning models was hard with Apache Spark on Amazon EMR? Join this workshop to learn how Amazon EMR Studio makes it simple to do these things. The workshop includes a walkthrough of a couple of examples with sample data so you can see how collaboration works with Amazon EMR Studio.

### Who is this workshop for?
This workshop is for data professionals to learn about Amazon EMR Studio to develop, visualize, and debug data engineering and data science workflows. This workshop will show how:

### How to use PySpark in EMR Studio to write and schedule some basic ETL
Utilize the prepared data for some data analysis and visualization
How to deploy your work to a publicly-hosted CloudFront website
You can expect this workshop to take approximiately 2 hours to complete. It will be helpful if you are familiar with Jupyter and PySpark, but not required.

### Will any costs be incurred?
If you run this workshop in your own account using the "Self Paced Labs" option, it will incur costs for various resources including:

* Amazon EMR Cluster
* Amazon VPC NAT Gateway
* Amazon CloudFront Distribution
* Amazon S3 Buckets
* When done with the workshop, ensure you clean up any resources you created as mentioned in the Summary

### What is Amazon EMR Studio
<b>Amazon EMR Studio</b> is an integrated development environment (IDE) that makes it easy for data scientists and data engineers to develop, visualize, and debug data engineering and data science applications written in R, Python, Scala, and PySpark.

EMR Studio provides fully managed Jupyter Notebooks and tools like Spark UI and YARN Timeline Service to simplify debugging. EMR Studio uses AWS Single Sign-On and allows you to log in directly with your corporate credentials without logging into the AWS console. Data scientists and analysts can install custom kernels and libraries, collaborate with peers using code repositories such as GitHub and BitBucket, or execute parameterized notebooks as part of scheduled workflows using orchestration services like Apache Airflow or Amazon Managed Workflows for Apache Airflow.

EMR Studio kernels and applications run on EMR clusters, so you get the benefit of distributed data processing using the performance-optimized Amazon EMR runtime for Apache Spark. Administrators can set up EMR Studio such that analysts can run their applications on existing EMR clusters or create new clusters using pre-defined AWS CloudFormation templates for EMR.

Some of the benefits of using Amazon EMR Studio:

* Simple to use
* Fully managed Jupyter Notebooks
* Easy to build production pipelines
* Simplified debugging

### Additional Resources
To learn more about Amazon EMR Studio, please check the following resources:

* <a href="https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-studio.html" target=_>Amazon EMR Studio Management Guide</a> 
* <a href="https://docs.aws.amazon.com/emr/latest/ManagementGuide/how-emr-studio-works.html" target=_>How Amazon EMR Studio Works</a>

## Lab 1: Data Exploration
In this lab, we'll use PySpark to explore some weather data, create a basic ETL, and schedule the notebook with parameters.

### Source Data
We'll use the <a href="https://registry.opendata.aws/noaa-gsod" target=_>NOAA Global Surface Summary of Day</a> dataset from the <a href="https://registry.opendata.aws" target=_>Registry of Open Data</a>. The dataset records daily weather observations from over 9000 weather stations across the globe. Each day's observation is stored in a CSV file for each weather station in a single S3 prefix. To begin, we'll read data from 2021 and use df.show() to get an idea of what it looks like.

## Lab 2: Data Analysis
In this lab, we'll use Python and common libraries like matplotlib and seaborn to draw a visualization of weather data.

### Overview
In the data exploration lab, we used PySpark to transform data from ~12,000 CSV files down to one single 22mb Parquet file. In this lab, we'll use the Python 3 kernel so we can draw a visualization of weather data over the course of a single calendar year.

## Lab 3: Continous Deployment
In this lab, we'll see how to use CodePipeline to deploy EMR Studio Notebooks to an Amazon S3-backed CloudFront website.

Associating a Git repository with your Workspace has the following benefits.

* <b>Version control</b> – Record code changes in a version-control system so that you can review the history of your changes and selectively reverse them.
* <b>Collaboration</b> – Share code with team members working in different Workspaces through remote Git-based repositories. Workspaces can clone or merge code from remote repositories and push changes back to those repositories.
* <b>Code reuse</b> – Many Jupyter notebooks that demonstrate data analysis or machine learning techniques are available in publicly-hosted repositories, such as GitHub. You can associate your Workspace with a GitHub repository to reuse the Jupyter notebooks contained in a repository.
* <b>DataOps</b> - Utilize continuous integration for testing your notebook code as well as continuous deployment to automatically deploy assets in your repository.

### Setup
This lab has a few steps.

1. Connect EMR Studio to CodeCommit
2. Build a CodePipeline to deploy our notebooks
3. Commit a new notebook and see it deployed

A CodeCommit repository was created for this lab, as well as a CloudFront distribution that will be used to provide a public URL for your notebooks. You will walk through creating the CodePipeline to see how to connect

* <a href="https://catalog.us-east-1.prod.workshops.aws/v2/workshops/ba48ba09-99ad-4113-b77c-0131ef9452c9/en-US/labs/continuous-deployment/codecommit-setup" target=_>3.1 CodeCommit Setup</a>
* <a href="https://catalog.us-east-1.prod.workshops.aws/v2/workshops/ba48ba09-99ad-4113-b77c-0131ef9452c9/en-US/labs/continuous-deployment/codepipeline-setup" target=_>3.2 CodePipeline Setup</a>
* <a href="https://catalog.us-east-1.prod.workshops.aws/v2/workshops/ba48ba09-99ad-4113-b77c-0131ef9452c9/en-US/labs/continuous-deployment/notebook-deployment" target=_>3.3 Continuous Deployment of Jupyter Notebooks</a>