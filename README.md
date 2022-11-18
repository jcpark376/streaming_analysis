# Data Modeling with Postgres: streaming_analysis

## Overview of Project

This project is part of [Udacity](https://www.udacity.com/)'s Data Engineering Nanodegree program. Here, I utilize music streaming data to create a database and construct a ETL pipeline utlizing PostgreSQL (Postgres).

The database is built for a hypothetical music streaming startup called Sparkify. Currently, the streaming data and song data are residing as JSON files in directories, and it is difficult to query the data to understand which songs users are listening to.

The new database will be a relational database that is optimized for analytical queries investigating song plays.

## How to Run Python Scripts
1. Run create_tables.py. This will initialize the PostgreSQL database according to the CREATE TABLE queries defined in sql_queries.py. If one runs into errors, check the credentials for connecting to Postgres in the first few lines of create_database().
2. Run etl.py. This will import, clean, and insert data in the data/ folder.

## Explanation of Files
**Python Files**
- create_tables.py: defines and generate tables in Postgres. This script utilizes scripts in sql_queries.py
- sql_queries.py: collection of all SQL queries used in repo, such as DROP TABLE, CREATE TABLE, INSERT INTO, etc.
- etl.py: run this file to ingest raw JSON files, transform them, and load them into the Postgres tables defined in create_tables.py.

**Jupyter Notebook Files**
- etl.ipynb: a playground/testing site for scripts that eventually went into etl.py
- test.ipynb: testing scripts live here

**Others**
- README.md: A readme file
- .gitignore: a .gitignore file

## Schema Design and ETL Pipeline Rationale
The database has 5 tables, one Fact table which is at the center of the schema and useful for analyses, and four Dimension tables that supply auxillary information for the Fact table.
**Fact Table**
- songplays
**Dimension Tables**
- users
- songs
- artists
- time
This organization fascilitates the query of songs that are/were streamed at a particular timepoint, which is the main business query that the analytics team has asked for.