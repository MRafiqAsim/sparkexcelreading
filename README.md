
# Exel File reading with spark on windows

Steps to follow to configure windows enviroment to read/write Exel file using spark excel and jupyter notebook with anaconda navigator.
## Step 1
Install Anaconda Navigator 
## Step 2
Download Spark from Spark website (version 3.3.2). https://spark.apache.org/downloads.html
## Step 3
Download Hadoop and winutil.exe  from github 
For winutils I copied files from this github repository:
https://github.com/cdarlint/winutils 
I used files from : hadoop-3.2.2/bin
## Step 4
unzip spark to C:\spark
inside spark folder at c:\spark create directory "hadoop"
	and then inside hadoop directory create directory "bin"
	now copy paste all the files from step 2 "hadoop-3.2.2/bin" to "c:\spark\hadoop\bin"

## Step 5
 install JDK 11 if not installed.
## Step 6
Enviroment variables:
	Set following enviroment variables :
##### 1- SPARK_HOME="C:\spark" (In users and systems variables)
##### 2-HADOOP_HOME="%SPARK_HOME%\hadoop" (In users and systems variables)
##### 3-PYSPARK_PYTHON="python"
##### 4-PYTHONPATH="%SPARK_HOME%\python;%SPARK_HOME%\python\lib\py4j-0.10.9.5-src.zip;%PYTHONPATH%" (In users and systems variables)
##### 5-In Users and Systems PATH variables add this to Path "C:\spark\bin"

## Step 7
open Anaconda CMD prompt and cd  to c:\spark 
## Step 8
##### 1-  run "bin\pyspark --master local[3] --driver-memory 2g --packages com.crealytics:spark-excel_2.12:3.3.1_0.18.5"
##### 2- it will create a file in users hidden directory ie "C:\Users\user_name\.ivy2\jars"
Copy all the jar files from this folder and paste in "C:\spark\jars"
## Step 9
Close Anaconda Navigator 
## Step 10
Open Anaconda Navigator and luanch notebook
## Step 11
now the excell reading spark-excel will work.
## Step 12 Sample File read
```python
from pyspark.context import SparkContext
from pyspark.sql.session import SparkSession
sc  = SparkContext.getOrCreate()
spark = SparkSession(sc)
df = spark.read.format('com.crealytics.spark.excel').option("header", "true").option("inferSchema", "true").load(r"C:\\Users\\abc\\myfile.xlsx\")"
df.show()
```
