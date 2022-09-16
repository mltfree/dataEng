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
> 	create or replace stage like_a_window_into_an_s3_bucket url = 's3://uni-lab-files'
> 	list @LIKE_A_WINDOW_INTO_AN_S3_BUCKET/this_;


