## Azure Synapse - Writing Parquet files to the Azure Data Lake with Synapse Spark.
** These are my own notes. **

1. Use Synapse Studio Notebook to Read and Write data. https://docs.microsoft.com/en-us/azure/synapse-analytics/spark/apache-spark-development-using-notebooks
2. Spark Pool is required for compute (Spark instance). https://docs.microsoft.com/en-us/azure/synapse-analytics/quickstart-create-apache-spark-pool-studio

3. Read Some data into a dataframe from the data lake. As long as you have permissions set correctly for data lake or storage access you can do a one line ready

```python
%%pyspark
data_path = spark.read.load('abfss://<containerspace>@<datalakestorename>.dfs.core.windows.net/Bike-Sharing-Dataset/landing/hour.csv', format='csv'
, header=True)

#display(data_path)
data_path.columns
```

4. Write back to data lake file path - parquet format with partitions as needed.

```python
%%pyspark
data_path.write.partitionBy('yr','mnth').parquet('abfss://tempspace@awdlsstudnn.dfs.core.windows.net/Bike-Sharing-Dataset/compressed/bikesharehour.parquet', mode = 'overwrite')
```


