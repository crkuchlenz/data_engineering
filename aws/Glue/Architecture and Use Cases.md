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

# What else should I keep in mind about AWS Glue?

AWS Glue is a scalable data integration service that streamlines the ETL process using built-in connectors. You can design complex workflows using crawlers, jobs, and initiations, and choose to author the jobs using code or visual transformations. The jobs can be deployed using AWS CloudFormation, which acts as infrastructure as code in JSON or YAML, and can be version-controlled in Bitbucket or GitHub. AWS Glue also offers centralized monitoring through a single pane of glass. This helps you check the status of your ETL pipeline and start, stop, and rerun jobs they have created. 

To learn more about other considerations for AWS Glue, expand each of the following seven categories.


## Partitioning
Partitioning is a technique that organizes related data together to minimize the amount of data scanned, thus improving query speed. One example is a sales database that is divided into partitions based on year, month, and day. To view sales from a specific day (for example, January 1, 2022), include a filter condition with the date, month, or year when writing scan queries. This way, you can limit the data scan for a particular year or month of data.



./Sales S3 Bucket

|--- Sales

    |--- Year=2022

        |--- Month=January

            |--- Day=1

            |--- Day=2 

            |--- Day=3

        |--- Month=February

    |--- Year=2021

 

By partitioning data in the Amazon S3 data lake, AWS Glue can scan only the data that matches the transformation logic. The AWS Glue crawler or jobs determine which data to process based on the underlying schema and partitioning strategy. If there are no new partitions, then there is no need to run the AWS Glue crawler. But if the schema has partitions that are added hourly or daily, the crawler will run with the schedule to keep the Data Catalog up to date with new data. To maximize performance and minimize cost, scan only the necessary data. This can be accomplished by implementing a targeted partitioning strategy focusing on specific columns or partitions.


## Run locally first
Experienced developers believe developing and testing ETL code for their business logic locally is fast and cost-effective, even in present time. AWS Glue provides options for local development through a Docker image and the AWS Glue Studio ETL libraries. Additionally, users can test their scripts remotely using AWS Glue interactive sessions in AWS Glue Studio.


## Using Auto Scaling for AWS Glue
With the AWS Glue Auto Scaling feature, ETL jobs can dynamically adjust the number of workers based on the processing demand for complex transformations. When the demand decreases, the number of workers returns to its original state. By doing this, developers don’t have to hardcode workers needed for their jobs. This feature is available in AWS Glue version 3.0 or higher.



With Auto Scaling activated, AWS Glue can do the following: 

- AWS Glue will automatically add and remove workers from the cluster, based on the parallelism of each stage or micro-batch of the job run.
- This eliminates the need to experiment manually with different worker configurations, with AWS Glue selecting optimal resources for your workload.
- You can monitor the cluster size during the job run by viewing CloudWatch metrics on the job run details page in AWS Glue Studio.
> For more information about AWS Glue Auto Scaling, see Using Auto Scaling for AWS Glue([opens in a new tab](https://docs.aws.amazon.com/glue/latest/dg/auto-scaling.html)).


## Compression and file format
Compressing your data conserves storage space and enhances the performance of distributed processing by minimizing network traffic between Amazon S3, AWS Glue, and other AWS services. Choosing a file format that supports compression, such as the columnar Parquet format, can improve performance. It is usually more efficient to work with fewer larger files, rather than multiple smaller files, when querying data stored in Amazon S3. By properly partitioning, compressing, and formatting your data, you can maximize the capabilities of query engines like Amazon Athena and Amazon Redshift Spectrum. This can help lead to faster query performance and reduced costs.


## Use job bookmarks: Incremental processing
AWS Glue has a mechanism for tracking the records processed in each job, known as job bookmarks. These bookmarks persist state information from previous job runs and help prevent reprocessing of old data. Using job bookmarks, developers can efficiently process only new or incremental files when rerunning a job. This provides efficient maintenance of state information and optimized processing.


## Security and encryption of data
Data protection is a key factor to consider when implementing real-world projects. To ensure the security of your data, AWS Glue offers various encryption options, including encryption at rest and in motion. When using AWS Glue to author jobs and develop scripts, your data can be encrypted at rest. Additionally, metadata stored in the Data Catalog can be encrypted using keys from the AWS Key Management Service (AWS KMS). SSL encryption is also available for data in motion through AWS Glue, and you can configure encryption settings for crawlers, ETL jobs, and development endpoints.


## Job monitoring
Monitoring production in AWS Glue jobs is an important part of maintaining the reliability, availability, and performance of AWS Glue. You can use the following automated monitoring tools to watch AWS Glue. Further details can be found in the resources section. 

- Amazon EventBridge
- Amazon CloudWatch Logs
- AWS CloudTrail

## Amazon Q Developer
AWS Glue can be integrated with Amazon Q Developer, a coding companion. With this integration, you can develop code quickly and conveniently, which can help speed up your data preparation for analytics and ML. When you use AWS Glue Studio notebooks to write code in Python, or even just type in English, Amazon Q Developer provides you with real-time recommendations. You can then either accept the top suggestion, view more suggestions, or continue writing your own code.


> For more information on using Amazon Q Developer with AWS Glue, see Amazon Q data integration in AWS Glue([opens in a new tab](https://aws.amazon.com/blogs/big-data/build-data-integration-jobs-with-ai-companion-on-aws-glue-studio-notebook-powered-by-amazon-codewhisperer/)).


## Transactional data lake
AWS Glue for Apache Spark now supports three open-source data lake storage frameworks: Apache Hudi, Apache Iceberg, and Linux Foundation Delta Lake. These frameworks provide consistent reading and writing of data in Amazon S3. They streamline incremental data processing in data lakes built on Amazon S3. This removes the need for a separate connector and reduces configuration steps in AWS Glue for Apache Spark jobs. With these frameworks, you can do time-travel queries; atomicity, consistency, isolation, and durability (ACID) transactions; streaming ingestion; change data capture; upserts; and deletes.


> For more information, see Using Data Lake Frameworks with AWS Glue ETL Jobs([opens in a new tab](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-datalake-native-frameworks.html)).

