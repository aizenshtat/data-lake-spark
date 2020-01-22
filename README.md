# Project: Data Lake

## Purpose of the project
A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The task is to build an ETL pipeline that extracts their data from S3, processes them using Spark, and loads the data back into S3 as a set of dimensional tables. This will allow their analytics team to continue finding insights in what songs their users are listening to.

## Project Datasets
Two input datasets are present:

### Song Dataset
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. 
### Log Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings.

## ETL Process and the Database Schema
Using the song and log datasets, a star schema, optimized for queries on song play analysis is created. This includes the following tables:

### Fact Table
1. songplays - records in log data associated with song plays i.e. records with page NextSong
2. songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
### Dimension Tables
1. users - users in the app
2. user_id, first_name, last_name, gender, level
3. songs - songs in music database
4. song_id, title, artist_id, year, duration
5. artists - artists in music database
6. artist_id, name, location, lattitude, longitude
7. time - timestamps of records in songplays broken down into specific units
8. start_time, hour, day, week, month, year, weekday

## Project Files
The whole ETL process consists of two files:
* etl.py - reads data from S3, processes that data using Spark, and writes them back to S3
* dl.cfg - contains AWS credentials (shouldn't be shared publicly)