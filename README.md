# Documenting my data eng learnings
___
### Snowflake Learnings 
> https://www.snowflake.com/en
> https://learn.snowflake.com/courses/course-v1:snowflake+ESS_DWW_101+2021/about
> Certification: https://www.credly.com/badges/535d8474-ebe0-40c7-8855-4ee8c62c43ac/public_url

#### Key functions of snowflake
> 1) Snowflake provides an easy way to manage your org's data
> 2) You can setup warehouses, databases, and tables
> 3) You can also easily manage populating data from external sources like an AWS S3 bucket 


#### Eg. Setting up a window to a staging env.  
> create or replace stage like_a_window_into_an_s3_bucket url = 's3://uni-lab-files'
> list @LIKE_A_WINDOW_INTO_AN_S3_BUCKET/this_;

#### Eg. loading data from a staging env
> copy into vegetable_details_soil_type
> from @like_a_window_into_an_s3_bucket
> files = ( 'VEG_NAME_TO_SOIL_TYPE_PIPE.txt')
> file_format = ( format_name=PIPECOLSEP_ONEHEADROW );

#### Eg. Creating a file format for laoding data
> CREATE OR REPLACE FILE FORMAT LIBRARY_CARD_CATALOG.PUBLIC.XML_FILE_FORMAT 
> TYPE = 'XML' 
> COMPRESSION = 'AUTO' 
> PRESERVE_SPACE = FALSE 
> STRIP_OUTER_ELEMENT = TRUE 
> DISABLE_SNOWFLAKE_DATA = FALSE 
> DISABLE_AUTO_CONVERT = FALSE 
> IGNORE_UTF8_ERRORS = FALSE; 
  
