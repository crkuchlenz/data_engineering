# How is AWS Glue used to architect a cloud solution?
With AWS Glue, you can identify and build a technical data catalog for various data storage locations. You can use this data catalog as input and then carry out ETL or extract, load, transform (ELT) processes based on their requirements. The following architecture displays the typical pattern of connecting to data sources using connectors. Later, crawl the data to identify the schema, clean and standardize, and author the ETL process to generate raw data. Then, use the same ETL utilities provided by AWS Glue to create refined data. This data can finally be consumed through analytical query engines like Amazon Athena, Amazon Redshift, and Amazon QuickSight.

1. **Data source**: Users can connect to various data sources using AWS Glue. These data sources can be popular relational databases with AWS or outside of Amazon Web Services (AWS). Data sources can also be flat files or streaming sources. AWS Glue uses built-in connectors and crawlers to automatically detect the data type and register the schema in the Data Catalog.
2. **AWS Glue connections**:AWS Glue saves connection objects for specific data stores with login credentials, URIs, and virtual private cloud (VPC) details. It supports popular data stores like Amazon Redshift, Amazon Aurora, SQL servers, MySQL, MongoDB, and PostgreSQL through Java Database Connectivity (JDBC) connections, and many more. Users can use marketplace connectors or custom connectors for non-built-in data stores.
3. **AWS Glue connections**:AWS Glue saves connection objects for specific data stores with login credentials, URIs, and virtual private cloud (VPC) details. It supports popular data stores like Amazon Redshift, Amazon Aurora, SQL servers, MySQL, MongoDB, and PostgreSQL through Java Database Connectivity (JDBC) connections, and many more. Users can use marketplace connectors or custom connectors for non-built-in data stores.
4. **Data Catalog**:AWS Glue offers a technical metadata store so you can store, classify, and define data schema. Data Catalog tracks metadata changes as data evolves, which you can share with other analytics services. It holds table information, such as schema, properties, and data format. It also works with services like AWS Identity and Access Management (IAM) and AWS Lake Formation to control table and database access.
5. **AWS Glue Schema Registry**: With AWS Glue Schema Registry, you can manage and enforce schemas on your data-streaming applications using convenient integrations. These integrations include Apache Kafka, Amazon MSK, Amazon Kinesis Data Streams, Amazon Kinesis Data Analytics for Apache Flink, and AWS Lambda.
6. **DataBrew**: DataBrew is a visual data preparation tool that helps you clean, enrich, format, and normalize datasets using over 250 built-in transformations. Users can create a recipe for a dataset using the transformations of their choice, and then reuse that recipe repeatedly on different collections of data.
7. **AWS Glue Jobs**: AWS Glue Jobs provides a managed infrastructure for orchestrating ETL workflows. Users can create jobs in AWS Glue that automate their scripts to extract, transform, and transfer data to different locations. These jobs can be scheduled or launched by events, such as the arrival of new data, and they can also be chained together.
8. **Data store and targets**: AWS Glue provides access to various data sources and targets, including Amazon Simple Storage Service (Amazon S3) and databases on AWS or on premises. It can even access any sources that offer JDBC utility for connections. 
> For a full list of supported connections using AWS Glue crawler, see Which Data Stores Can I Crawl?
9. **AWS analytics services**: AWS offers the following analytics services:
- Athena is an interactive query service that makes it effortless to analyze data in Amazon S3 and data sources. 
- Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud.
- QuickSight is a scalable, serverless, embeddable, ML-powered business intelligence (BI).

![image](https://github.com/user-attachments/assets/f2f37654-47f4-4b3b-b56d-591e96d02f68)


# What are the basic technical concepts of AWS Glue Studio?
To learn more about the basic technical concepts of AWS Glue Studio, expand each of the following ten categories.

## Connection
An AWS Glue connection is an object in the Data Catalog that holds information such as login credentials, URI strings, VPC details, and more for a specific data store. AWS Glue components, such as crawlers, jobs, and development endpoints, use these connections to access particular data stores. Connections can be used for source and target data stores, and the same connection can be used multiple times by various crawlers or ETL jobs. For more information, see Adding an AWS Glue Connection(opens in a new tab).

## Crawler
An AWS Glue crawler can connect to various sources, identify their schema, and categorize them into data formats. They can also create metadata tables in the Data Catalog by using built-in data classifiers. For more information about crawlers, see Defining Crawlers in AWS Glue(opens in a new tab).

## Datastore, data source, data target
A data store refers to physical storage where data is meant to persist permanently. An example of data stores in AWS would be Amazon S3 buckets and relational databases like Amazon Relational Database Service (Amazon RDS) for MySQL. These can serve as the input for processing or transformation. A data target refers to a data store where a process or transformation is output-written.

## AWS Glue interactive sessions
With AWS Glue interactive sessions, users can build and test data preparation needed for analytics applications. These sessions provide self-managed notebooks, which help developers write one-time queries or transformations that can be used to prepare data for ML. AWS Glue interactive sessions offer notebook editors, which can be deployed locally or remotely. Doing it this way can assist developers with quick development and testing time. AWS Glue integrates with AWS Glue Studio and Amazon SageMaker Studio for notebook management. For more information about AWS Glue interactive sessions, see Getting Started with AWS Glue interactive sessions(opens in a new tab).

## DynamicFrame
A DynamicFrame is a distributed table that facilitates the storage of nested data, such as structures and arrays. It does this by cleaning and reorganizing semi-structured datasets like JSON, Avro, and Apache logs. With DynamicFrame, there is no need for an upfront schema. The schema can be inferred without interruption so that transformations occur in a single pass. It is not difficult to handle unexpected changes because it tracks new fields and inconsistent changes in data types with choices, automatically marking and separating error records.

## Job
The business logic necessary to carry out ETL work consists of a transformation script, data sources, and data targets. After the user has completed authoring the transformation, it can be initiated through job-based triggers, which can be scheduled or based on events.

## File formats
AWS Glue supports two types of file formats:

- **Apache Parquet** format is a type of file format that structures data in a columnar format, rather than a row-based format like a CSV or Microsoft Excel file. Apache Parquet format is optimal for analytical engines like Athena or Amazon Redshift Spectrum to query over.
- AWS Glue now supports Apache Hudi, Apache Iceberg, and Delta Lake, which gives transactional capabilities to the data lake on Amazon S3.

## Table
The metadata that represents user data is known as the table definition. Regardless of whether your data is stored in an Amazon S3 file, an Amazon RDS table, or elsewhere, a table defines the schema of that data. The table in the Data Catalog consists of information such as column names, data type definitions, partition details, and other metadata about the base dataset. The schema of your data is reflected in the AWS Glue table definition, while the actual data stays in its original data store (whether that be a file or a relational database table). The AWS Glue tables, which are cataloged in Data Catalog, can be used as sources or targets while creating an ETL job.

## Transform
Transform is the code logic that is used to manipulate data into a different format and translate that into business logic.

## AWS Glue triggers
A trigger, which initiates or starts an ETL job, can be defined based on a scheduled time or an event.


# What are the basic technical concepts of AWS Glue DataBrew?
To learn about the technical concepts of AWS Glue DataBrew, expand each of the following nine categories.

## Dataset
In DataBrew, a dataset refers to data that can be obtained from various sources, such as an Amazon S3 file, a supported JDBC data source, or the Data Catalog. The dataset also includes information on how DataBrew can access the data if it is not directly uploaded.

## Profiling
DataBrew validates data by running a series of evaluations to identify trends and spot any irregularities by accessing data directly from the data lake, data warehouses, and databases.

## Data lineage
Data lineage is a visual representation of all the data transformations, from origin to target.

## Data quality
A data-quality process can help ensure the accuracy of your data. You establish a set of guidelines, known as a ruleset, and enforce the data to identify and correct the faulty data. This ruleset includes comparisons between actual data values and desired values. The entire ruleset is considered valid if the criteria set in the ruleset are met. After checking the results of each rule, users can make necessary adjustments to their data. After changes have been made, users can reevaluate the ruleset multiple times.

Examples of rules include the following:
- The value in column APY is between 0 and 100.
- The number of missing values in column group_name doesn't exceed five percent.

## Recipes
In DataBrew, a recipe is a sequence of operations used to transform the data. The steps in a recipe can be tested on a data sample before being applied to the entire dataset.

## Project
DataBrew provides a centralized data analysis and manipulation platform through projects. A project consists of two key components:
- A dataset that grants read-only access to the source data
- A recipe that uses DataBrew transformation actions on the dataset
The DataBrew console and interface is user friendly and interactive, encouraging exploration and testing of different transformations to evaluate their effects on the data.

## Jobs
The job feature in DataBrew serves two main functions:
- A DataBrew recipe job that runs the transformations on a dataset
- A DataBrew profile job that inspects a dataset and generates a comprehensive summary of the data
Profile jobs produce their findings to Amazon S3 and offer essential insights to assist in identifying appropriate data preparation actions. Use a DataBrew recipe job to clean and standardize the data in a dataset and output it to a designated location. Running a recipe job does not modify the source data or the dataset. The job accesses the source data in a read-only manner, and the output is sent to the specified location on Amazon S3, the Data Catalog, or a supported JDBC database.

## File type
DataBrew supports specific file types and formats, including comma-separated values (CSV), Microsoft Excel workbook, JSON documents and JSON lines, Apache Optimized Row Columnar (ORC), and Apache Parquet format.

## Transform
Transform is the set of instructions or algorithms used to transform your data into a different format.

# What are typical use cases for AWS Glue?
To learn more about uses cases for AWS Glue, expand the following five categories.

## Streamlined ETL development
AWS Glue ETL offers the benefits of data extraction, transformation, and load or store, without the need to manage infrastructure. Users can write their ETL scripts using Python or Scala, or use the auto-generate feature like auto scaling resources and workflow management. This makes AWS Glue a comprehensive data integration service.

Users can use Data Catalog to quickly discover and search across multiple AWS datasets without moving the data. After the data is cataloged, it is immediately available for search and query using Athena, Amazon EMR, and Amazon Redshift Spectrum.

## Technical data catalog to find data across multiple data stores
Users can use Data Catalog to quickly discover and search across multiple AWS datasets without moving the data. After the data is cataloged, it is immediately available for search and query using Athena, Amazon EMR, and Amazon Redshift Spectrum.

## Data quality, data preparation, and data profiling without coding
AWS Glue offers flexibility by providing users the opportunity to create custom data quality rules or use a set of recommended rules for quick data quality checks. Data quality in AWS Glue is integrated with CloudWatch for monitoring and alerting, in case of messy data. Additionally, AWS Glue users can use DataBrew, a no-code service for data statistics, cleaning, normalizing, and profiling. DataBrew comes with over 250 built-in transformations, providing data analysts with the option to prepare data for ML.

## Quick job orchestration and visualization with drag and drop
AWS Glue Studio is a convenient solution for rapidly creating and running AWS Glue ETL jobs, without having to manually write code. This feature provides a visual drag-and-drop editor that facilitates the manageable design of their complex data pipeline. It automatically generates the corresponding code for initiation. The built-in monitoring and dashboarding capabilities in AWS Glue Studio are also helpful for scaling and managing a large number of jobs. AWS Glue provides workflows that can be used to create and visualize complex ETL operations that involve multiple crawlers, jobs, events, or scheduled job or workflow triggers.

## Real-time data processing
Batch processing is a good option when the processed data is used or visualized at specific times, such as an end-of-day sales summary. However, in some cases, you might want to process and use data as soon as it becomes available. Examples include user login patterns, social media data, network logs, or clickstream data. In these situations, developers can use AWS Glue Streaming ETL to process real-time data. With AWS Glue Streaming ETL, you can create jobs that run continuously and consume data from streaming sources. These jobs can process the data in real time and load the processed data into Amazon S3 or JDBC data stores.


