# Introduction

AWS Glue is a serverless data integration service, which means that you only pay for usage and don't pay for idle time. With AWS Glue, data scientists, analysts, and developers can discover, prepare, and combine data for various purposes. Examples include analytics, machine learning (ML), and application development. AWS Glue provides visual and code-based interfaces for data integration activity and transforms data using built-in transformations. 
You can also quickly locate and access data through the AWS Glue Data Catalog. Data engineers and extract, transform, and load (ETL) developers can create, run, and monitor ETL workflows using AWS Glue Studio. Data analysts can use the no-code capabilities of AWS Glue DataBrew to enrich, clean, and normalize data without writing any code. Data scientists can use AWS Glue interactive notebooks to quickly start querying their data for interactive analytics, rather than spending months creating infrastructure.

## Which problems does AWS Glue solve?
To learn more about how AWS Glue streamlines many tasks, expand the following eight categories.

### Provisions and manages the lifecycle of resources
AWS Glue provisions the requested resources like servers, storage, and runtime environment that ETL jobs need. It also manages the lifecycle of these resources and removes them when they are not being used. AWS Glue maintains the resource pool from where requested capacity is allocated.

### Provides interactive tools
AWS Glue has tools for each persona for performing development activities that include no-code, low-code, and interactive tools, so it reduces development time.

### Auto-generates code
AWS Glue auto-generates code when built-in transformations are used, which is optimized for runtime and cost-effectiveness. It also provides features to upload the scripts to make migration more straightforward.

### Connects to hundreds of data stores
AWS Glue connects to hundreds of data stores, including Amazon Redshift, relational databases, MongoDB, and software as a service (SaaS) providers like Salesforce. It also exposes APIs to conveniently build your own connectors.

### Creates a data catalog for various data sources
AWS Glue provides the opportunity to create a data catalog for various data sources that could help search metadata and classify data. AWS Glue Data Catalog is used by multiple analytics services to work on the data.

### Identifies sensitive data using ML recognition patterns for PII
AWS Glue helps in identifying sensitive data using ML recognition patterns for personally identifiable information (PII). After identification, you can remediate them by redacting through string or cryptographic hashing.

### Manage and enforce schemas on data-streaming applications
Using AWS Glue, you can also manage and enforce schemas on data-streaming applications. Integrations with Apache Kafka and Amazon Kinesis help ensure that downstream systems are not affected by semantic changes in upstream systems.

### Offers data quality and automatic data scaling
AWS Glue offers data quality for creating and applying built-in rule types or custom rule types to clean and normalize your data. AWS Glue automatically scales as the volume of data increases, and it is integrated with Amazon CloudWatch for monitoring.

## What are the benefits of AWS Glue?
To learn more about the benefits of AWS Glue, expand each of the following five benefit categories.

### Faster data integration
With AWS Glue, developers have the flexibility to choose their preferred tool for data preparation and processing. This makes it possible to quickly deliver data for analytics, ML, and application development. By creating repeatable and reusable workflows, developers can streamline data integration and ETL processes, making collaboration on these tasks more efficient. 
Data engineers can develop and test your AWS Glue job scripts through multiple options: 

#### AWS Glue Studio console
- Visual editor
- Script editor
- AWS Glue Studio notebook

#### Interactive sessions
- Jupyter Notebook

#### Docker image
- Local development
- Remote development

#### AWS Glue Studio ETL library
- Local development

### Automate data integration at scale
AWS Glue uses crawlers to scan data sources, identify data format and metadata, register the data's schema, and generate code for transformations. It also provides workflows that developers can use to create streamlined and advanced pipelines for ETL tasks.

### No infrastructure to manage
AWS Glue helps you prepare and work on data without users needing to provision and maintain any infrastructure. This makes AWS Glue serverless, because AWS will manage and provision servers from a warm pool. It automatically scales resources up and down as required by AWS Glue jobs. By doing this, data engineers and developers can focus on writing business logic and creating complex workflows. AWS Glue works with continuous integration and continuous delivery (CI/CD) and also with alerting or monitoring services to make their workload self-service.

### Create, run, and monitor ETL jobs without coding
AWS Glue Studio provides straightforward creation, running and monitoring of ETL tasks for data transformation through a user-friendly drag-and-drop interface. It automatically generates code and offers built-in transformations from AWS Glue DataBrew that can assist with data cleaning and standardization. The processed data can then be used for analytical and ML purposes.

### Pay only for what you use
With AWS Glue, users pay only for the resources they consume. There's no upfront cost, and users are not charged for a start-up or shutdown time.

## How much does AWS Glue cost?
AWS Glue consists of various components. Each of these has a specific purpose and cost structure. Please note pricing can vary by AWS Region and can change. The following information is as of Q3 2023. 
To learn more about the costs of AWS Glue, expand each of the following eight categories. 

### AWS Glue ETL jobs and interactive sessions
With AWS Glue, there are no upfront fees or costs for maintaining infrastructure and no charges for starting up or shutting down. Users only pay for what they use, which means charges are only applied to job runs. The cost is based on an hourly rate that is rounded to the nearest second, calculated based on the number of DPUs used to run your ETL job. AWS Glue offers different worker types with varying capacities, including Standard, G.1X, G.2X, and G.025X. One DPU is equivalent to 4 vCPUs and 16 GB of memory.

Users can use AWS Glue interactive sessions for interactive ETL code development, but they will only incur charges if they decide to run some transformations as a job. The duration of the session determines the cost of interactive sessions and the amount of DPUs used. Interactive sessions can be set with adjustable idle timeouts, and are billed a minimum of 1 minute. Interactive sessions require a minimum of 2 DPUs, with a default of 5 DPUs.

AWS Glue Studio allows data previews to test your transformations during the job authoring process. Each AWS Glue Studio data preview session uses 2 DPUs, runs for 30 minutes, and stops automatically.

### Data Catalog and storage requests
With Data Catalog, you have a free tier to store a certain number of metadata objects such as tables, table versions, partitions, and databases. If you exceed this limit, you will incur charges based on the number of additional objects you store over the free tier. The pricing is applied on a per-object basis and is based on the number of objects exceeding the free-tier limit. It's important to note that the charges apply only to the Data Catalog and not to any other AWS services that you may use with it.

### AWS Glue crawlers
AWS Glue crawlers incur an hourly charge for discovering data and updating the Data Catalog based on the number of DPUs used. The crawler is billed in 1-second increments, with a minimum of 10 minutes for each crawl, and rounded up to the nearest second. Using AWS Glue crawlers is optional, and users can populate the Data Catalog directly through the API.

### DataBrew interactive sessions
DataBrew charges users for authoring on a per-session basis. A session is initiated when a DataBrew project is opened and users are billed for the total number of sessions used. Each session can last for 30 minutes and is billed in 30-minute increments. First-time users of DataBrew are offered the first 40 interactive sessions for free.

### DataBrew jobs
Users are charged an hourly rate based on the number of DataBrew workers used to run the job. By default, DataBrew allocates five workers to each job. There is a 1-minute billing duration for each job. 

### AWS Glue Flex execution
AWS Glue has introduced a new option that can help customers reduce the costs of their pre-production, testing, and non-critical data integration workloads by as much as 34 percent. This option is known as AWS Glue Flex execution, which utilizes spare capacity in AWS to run AWS Glue jobs.
 
### AWS Glue Data Quality
With AWS Glue Data Quality, users can standardize their data by comparing it with the source system and preserving the approved data for downstream use. AWS Glue automatically generates rule recommendations based on computed statistics of the data and uses these statistics to verify its accuracy. Additionally, custom rules can be created by writing logic using the straightforward Data Quality definition language.

### AWS Glue Schema Registry
A schema defines the structure and format of a data record. With AWS Glue Schema Registry, you can manage and enforce schemas on your data streaming applications using convenient integrations. These integrations include Apache Kafka, Amazon Managed Streaming for Apache Kafka, Amazon Kinesis Data Streams, Amazon Kinesis Data Analytics for Apache Flink, and AWS Lambda.
