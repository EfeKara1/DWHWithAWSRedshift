# DWHWithAWSRedshift

Data Warehouse with RedShift



### create_table.py is where you'll create your fact and dimension tables for the star schema in Redshift.
### etl.py is where you'll load data from S3 into staging tables on Redshift and then process that data into your analytics tables on Redshift.
### sql_queries.py is where you'll define you SQL statements, which will be imported into the two other files above.


A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

This project aims to build an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to.
Table of Content

    Requirements and Framework
    Data-Source
    To-Run
    Database Schema

Requirements and Framework

    Python 3 (psycopg2 | pandas | json)
    AWS SDK (boto3)
    Jupyter (ipython-sql)

Data Source

The source data is in log files given the Amazon s3 bucket at s3://udacity-dend/log_data and s3://udacity-dend/song_data containing log data and songs data respectively. Log files contains songplay events of the users in json format while song_data contains list of songs details.
To Run
AWS set-up

    IAM creation:

    Create IAM user
    Create IAM role with AmazonS3ReadOnlyAccess access and get secruity credentials
    Get IAM ARN

    Redshift Cluster set up for ETL pipeline:

    Cluster: 4x dc2.large nodes
    Location: US-West-2 

Scripts

    dwh.cfg: Fill in AWS acces key (KEY) and secret (SECRET) """It's been removed because of security reasons."""
    create_tables.py: Retrieve query from sql_queries which works create the DB to AWS Redshift
    etl.py :Process all the input data to the DB
    sql_queriespy: Contain create, drop, and insert queries which work on staging tables and analytics tables.

Database Schema

Here we use a star schema for Sparkify analytics database. It is a denormalized database that provides the benefits of simplified and more performant queries by reducing the number of joins between tables.
Start design means that it has one Fact Table having business data, and supporting Dimension Tables. The Fact Table answers one of the key questions: what songs users are listening to.
DB Schema Staging Tables:

    staging_events:
    staging_songs:

Analytics Tables:

    Fact Tables

        songplays: Records in log data associated with song plays

    Dimensiontables:

        users: Users in the app songs: Songs in music database artists: Artists in music database time: Timestamps of records in songplays broken down into specific units




