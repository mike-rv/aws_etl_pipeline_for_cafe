# group-1-data-engineering-final-project

# cafe-etl-group-project

## Project Description:
This project aims to design and implement an ETL(Extract, Transform, Load) pipeline to acquire, store, process and visualise analytics from collated data across London fron a Chain Cafe business, who want the opportunity to collect and analyse data from their customers. The application makes use of common distributed computing technologies for working with large volumes of data at scale (S3, AWS Lambda), and web frameworks (Cloudwatch, Grafana) for the visualisation of the data. The project also makes use of Containerisation, using Docker and an Amazon EC2 instance to aid development and deployment.

### 1. Project Outline
The café that we had previously developed a CLI application for has experienced unprecedented growth and has expanded to multiple stores across the country. The company is experiencing issues with collating and analysing the data produced at each branch because their technical setup is limited. We have been given the task of providing consultation on what they need to do in order to grow their technical offerings, so that they can continue to accelerate their growth. The company currently has no way of identifying trends, meaning they are potentially losing out on major revenue streams.
The software currently being used only generates reports for single branches.

**The development of an end to end soultion comprised of:**

1. Building a fully scalable ETL (Extract, Transform, Load) pipeline to handle large volumes of transactional data for the business. 
2. This pipeline will collect all the transaction data generated by each individual café and place it in a single location. Application monitoring software will be used to produce operational metrics, such as system errors, up-time and more.
3. Data analytics software will be used to create Business Intelligence analytics for the client.


### 2. Project Design
![Untitled Diagram-2](https://user-images.githubusercontent.com/116551424/213489993-8672d6db-d6fc-44f2-901a-8f87b1d50eda.jpg)



### 3. Project Implementation

## Initial Setup, Development Environment and Docker
The early draft of our ETL project consisted of pushing our data on a locally hosted database. Using PostgreSQL to query and manipulate tables. This would provide the a local perspective to how the ETL project would function before we moved on to AWS for our final iteration of the the pipeline. 

Externalize Database Connectivity Information
Creating a file with list of tables to be loaded
Reading table list using Pandas


### Normalisation + schema
The aim was to make querying as straightforward as possible. We ensured that the normalisation process allowed us to accurately query the databases and retrieve the relevant information. The further 
we normalise, the less query flexibility we achieve. As a result, we did not go further than 3NF. This allowed us to reduce redundant data and data inconsistency. Hence, we could see what our tables would look like, what we should remove, and how we should transform our data. 

![image](https://user-images.githubusercontent.com/115237595/206580167-d9c98840-6106-4621-b368-28f28d4d66d0.png)

## Data Transformation
We were given an example CSV file, 2021-02-23-isle-of-wight.csv, which replicated the type of data the pipeline would be handling. The CSV had a lot of PII, so we created a function where we pass in the CSV as a parameter, and the name, card details and card type columns would be removed. It then returns a list of the extracted data.


- hashing
- df etc.

## AWS

Amazon Web Services is at the core of our ETL pipeline for how we dropped data, [.csv files] into buckets that would automatically go through transformation with our lambda. The cloudformation process and EC2 for hosting the site were all thanks to AWS ability to scale and process the data through connected services. Additional functions included managing permission for who could access the database using SSM. We used SQS for automated messaging within the AWS environment to ensure that we could verify when data was successfully queried.


## Database

The outcome of transformed data were loaded into our Redshift database where sensitive information was removed and our order_id was hashed to provide unique identifiers that would prevent duplication conflicts.


## Data Visualisation 

We used docker's plug-in Grafana that we hosted on our EC2 for data visualisation. The tools that we drew from realtime on our live database on AWS Redshift provided many opportunities to display data appropriately.
It can also be used to moniter our website's internal metric for maintanince purposes.
We were able to query different metrics that were relevant for our business intellgence clients to pull from. Ranging from best performing cafe,worst performing product, average spend and so on. This provided the final part of our ETL process.


## Automation

Initially, we used a local script using git commands to initiate the deploy process. Each time the code was altered, the updates were automatically applied on AWS. We later updated this model with Github Actions. This CI/CD process allowed us to automate the deploy process via the cloud and was able to verify if the changes were functional or not upon completion.


## Features:
- [Grafana](https://grafana.com/) for Data Visualisation and EC2 monitoring.

- [Docker](https://www.docker.com/) for running a Grafana container within AWS EC2.

- [GitHub Actions](https://github.com/features/actions) for automating the CI/CD deploy process online.

AWS Services:

- [AWS Redshift](https://aws.amazon.com/redshift) for Data Warehousing.

- [AWS SQS](https://aws.amazon.com/sqs/) for Load Queue Messaging. 

- [AWS EC2](https://aws.amazon.com/ec2/features/) for running an instance to host Grafana site.

- [AWS SSM](https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent.html) for managing sensitive information.

- [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) for running code to allow for the Extract, Transform and Load processes to function.

- [AWS Cloudformation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) creates a 'stack' to set up our resources.

- [AWS Cloudwatch](https://aws.amazon.com/cloudwatch/features/) allows for monitoring performance and operational data in logs.

- [AWS IAM](https://aws.amazon.com/iam/features/?nc=sn&loc=2) attaches policy to grant access permissions.

Grafana plugins for visualisation includes:
- [Redshift](https://grafana.com/grafana/plugins/grafana-redshift-datasource/?tab=installation) 
for pulling data from AWS
- [Cloudwatch](https://grafana.com/docs/grafana/latest/datasources/aws-cloudwatch/) for Lambda / EC2 Metrics

Python3, Pandas and Git were also used.


### Ways of working
(insert Jira Board screenshot)
The project consisted of five sprints, where each sprint is a week in length. Using agile methodolgy we assigned priority and difficulty of task [issue points] to our weekly sprint goals. Each person was assigned a task by the SCRUM master and we reviewed it as a team and with the product owner. We had weekly friday retros to discuss and improve our collabtaive efforts. We also had daily stand ups at the start of the day and stand outs at the end of the day.



## Conclusion


Reading table list using Pandas
lambda
clouddformation ec2
normalisation
