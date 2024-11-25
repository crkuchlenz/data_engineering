# Table Of Contents

## Chapter 1
What Is Data Engineering, defines data engineering. It will introduce you to the skills, roles, and responsibilities of a data engineer. You will also learn how data engineering fits in with other disciplines, such as data science.

## Chapter 2
Building Our Data Engineering Infrastructure, explains how to install and configure the tools used throughout this book. You will install two databases – ElasticSearch and PostgreSQL – as well as NiFi, Kibana, and, of course, Python.

## Chapter 3
Reading and Writing Files, provides an introduction to reading and writing files in Python as well as data pipelines in NiFi. It will focus on Comma Seperated Values (CSV) and JavaScript Object Notation (JSON) files.

## Chapter 4
Working with Databases, explains the basics of working with SQL and NoSQL databases. You will query both types of databases and view the results in Python and through the use of NiFi. You will also learn how to read a file and insert it into the databases.

## Chapter 5
Cleaning and Transforming Data, explains how to take the files or database queries and perform basic exploratory data analysis. This analysis will allow you to view common data problems. You will then use Python and NiFi to clean and transform the data with a view to solving those common data problems.

## Chapter 6
Project – Building a 311 Data Pipeline, sets out a project in which you will build a complete data pipeline. You will learn how to read from an API and use all of the skills acquired from previous chapters. You will clean and transform the data as well as enrich it with additional data. Lastly, you will insert the data into a warehouse and build a dashboard to visualize it.

## Chapter 7
Features of a Production Data Pipeline, covers what is needed in a data pipeline to make it ready for production. You will learn about atomic transactions and how to make data pipelines idempotent.

## Chapter 8
Version Control Using the NiFi Registry, explains how to version control your data pipelines. You will install and configure the NiFi registry. You will also learn how to configure the registry to use GitHub as the source of your NiFi processors.

## Chapter 9
Monitoring and Logging Data Pipelines, teaches you the basics of monitoring and logging data pipelines. You will learn about the features of the NiFi GUI for monitoring. You will also learn how to use NiFi processors to log and monitor performance from within your data pipelines. Lastly, you will learn the basics of the NiFi API.

## Chapter 10
Deploying Your Data Pipelines, proposes a method for building test and production environments for NiFi. You will learn how to move your completed and version-controlled data pipelines into a production environment.

## Chapter 11
Project – Building a Production Data Pipeline, explains how to build a production data pipeline. You will use the project from Chapter 6 and add a number of features. You will version control the data pipeline as well as adding monitoring and logging features.

## Chapter 12
Building an Apache Kafka Cluster, explains how to install and configure a three-node Apache Kafka cluster. You will learn the basics of Kafka – streams, topics, and consumers.

## Chapter 13
Streaming Data with Kafka, explains how, using Python, you can write to Kafka topics and how to consume that data. You will write Python code for both consumers and producers using a third-party Python library.

## Chapter 14 
Data Processing with Apache Spark, walks you through the installation and configuration of a three-node Apache Spark cluster. You will learn how to use Python to manipulate data in Spark. This will be reminiscent of working with pandas DataFrames from Section 1 of this book.

## Chapter 15
Project – Real-Time Edge Data – Kafka, Spark, and MiNiFi, introduces MiNiFi, which is a separate project to make NiFi available on low-resource devices such as Internet of Things devices. You will build a data pipeline that sends data from MiNiFi to your NiFi instance.

The Appendix teaches you the basics of clustering with Apache NiFi. You will learn how to distribute data pipelines and some caveats in doing so. You will also learn how to allow data pipelines to run on a single, specified node and not run distributed while in a cluster.
