## Azure Synapse - Writing Parquet files to the Azure Data Lake with Synapse Spark.

1. Use Synapse Studio Notebook to Read and Write data. https://docs.microsoft.com/en-us/azure/synapse-analytics/spark/apache-spark-development-using-notebooks
2. Spark Pool is required for compute (Spark instance). https://docs.microsoft.com/en-us/azure/synapse-analytics/quickstart-create-apache-spark-pool-studio

3. Read Some data into a dataframe from the data lake. As long as you have permissions set correctly for data lake or storage access you can do a one line ready

```pyspark
data_path = spark.read.load('abfss://tempspace@awdlsstudnn.dfs.core.windows.net/Bike-Sharing-Dataset/landing/hour.csv', format='csv'
## If header exists uncomment line bellow
, header=True)
```

