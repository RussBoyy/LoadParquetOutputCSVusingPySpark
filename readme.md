**How to load a parquet file into a PySpark dataframe using S3 and EMR, and write the dataframe back to S3 in .csv format**

You will need a S3 bucket and a EMR cluster to complete this simple excerise.  Your EMR cluster will need to assume a role that has write permissions to S3.

The following statement will load data into a dataframe called museums from AWS S3.  Note: replace the value [bucket] with the name of your s3 bucket.  

<code>val museums = spark.read.option("header",true).option("inferSchema",true).parquet("s3://[bucketname]")</code>

The following statement will output the contents of the museums dataframe to S3 in .csv format.

<code>museums.write.option("header",true).mode("overwrite").csv("s3://[bucketname]/OutputfromEMR")</code>

