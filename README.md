# Documenting my data eng learnings
___
## Snowflake Learnings 
> 1) https://www.snowflake.com/en
> 2) https://learn.snowflake.com/courses/course-v1:snowflake+ESS_DWW_101+2021/about
> 3) Certification: https://www.credly.com/badges/535d8474-ebe0-40c7-8855-4ee8c62c43ac/public_url

#### Key functions of snowflake
> 1) Snowflake provides an easy way to manage your org's data
> 2) You can setup warehouses, databases, and tables
> 3) You can also easily manage populating data from external sources like an AWS S3 bucket 


#### Eg. Setting up a window to a staging env.  
	create or replace stage like_a_window_into_an_s3_bucket url = 's3://uni-lab-files'
	list @LIKE_A_WINDOW_INTO_AN_S3_BUCKET/this_;

#### Eg. loading data from a staging env
	copy into vegetable_details_soil_type
	from @like_a_window_into_an_s3_bucket
	files = ( 'VEG_NAME_TO_SOIL_TYPE_PIPE.txt')
	file_format = ( format_name=PIPECOLSEP_ONEHEADROW );

#### Eg. Creating a file format for laoding data
	CREATE OR REPLACE FILE FORMAT LIBRARY_CARD_CATALOG.PUBLIC.XML_FILE_FORMAT 
	TYPE = 'XML' 
	COMPRESSION = 'AUTO' 
	PRESERVE_SPACE = FALSE 
	STRIP_OUTER_ELEMENT = TRUE 
	DISABLE_SNOWFLAKE_DATA = FALSE 
	DISABLE_AUTO_CONVERT = FALSE 
	IGNORE_UTF8_ERRORS = FALSE; 
  
___
## Airflow Learnings 
> 1) https://airflow.apache.org/
> 2) Learnt a ton from https://www.youtube.com/watch?v=IH1-0hwFZRQ, and getting setup on docker https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html

#### Key functions of airflow
> 1) It all starts off with a DAG, where you define criteria like the start date of the operations, the frequency, whether you want emails on error etc. 
> 2) You then define operations which can be bash commands, python functions, or sensors. See a complete list here: https://airflow.apache.org/docs/apache-airflow/stable/operators-and-hooks-ref.html
> 3) Finally you tie the dependencies together, eg. t1 >> t2

#### Eg. DAG that outputs a certain action based on some conditions 
> 1) Based on https://www.youtube.com/watch?v=IH1-0hwFZRQ
> 2) ![Airflow dag](/assets/imgs/airflow_DAG1.png "airflow_DAG1") 
