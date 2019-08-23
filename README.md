## Purpose of this database in context of the startup, Sparkify, and their analytical goals
A music streaming startup called Sparkify wants to analyze the data they have been collecting on songs and user activity on their new music streaming app. The data is provided in JSON format in a S3 bucket, which gives information on artists and songs, and the user actions. The project is realised with Apache Spark.

## State and justify your database schema design and ETL pipeline.
The ETL job processes the song files then the log files. 
1. The song files are listed and iterated over entering relevant information in the artists and the song folders in parquet.
2. The log files are filtered by the NextSong action. The subsequent dataset is then processed to extract the date , time , year etc. fields and records are then appropriately entered into the time, users and songplays folders in parquet for analysis.
In our project we have 1 fact tables (songplays), which consists of the primary keys of each dimension table but also other attributes. There are 4 dimension tables (users, songs, artists, time), each of them consists of the primary key, which links to the fact table, and the respective attribute describing the dimension.

There are used 3 different files to create this project (1 notebook documents (.ipynb), 1 config script and 1 python script (.py)):
1. **execute.ipynd** is a python script to call following 3 python scripts and start the etl: etl.py, create_tables.py, sql_queries.py
2. **etl.py** is a python script to load the data from song_data and log_data into the star schema database. 
3. **dl.cfg** is a config script that holds the information on AWS credentials.





