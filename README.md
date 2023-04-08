#Spark SetupSteps with Excel Plugin:
0- Install Anaconda Navigator 
1- Download Spark from Spark website (version 3.3.2). 
https://spark.apache.org/downloads.html
2- Download Hadoop and winutil.exe  from github 
https://github.com/cdarlint/winutils 
we will use files from : hadoop-3.2.2/bin
3- unzip spark to C:\spark
4- inside spark folder at c:\spark create directory "hadoop"
	and then inside hadoop directory create directory "bin"
	now copy paste all the files from step 2 "hadoop-3.2.2/bin" to "c:\spark\hadoop\bin"
	
5- install JDK 11 if not installed.
6- Enviroment variables:
	Set following enviroment variables :
	1-SPARK_HOME="C:\spark" (In users and systems variables)
	2-HADOOP_HOME="%SPARK_HOME%\hadoop" (In users and systems variables)
	3-PYSPARK_PYTHON="python"
	4-PYTHONPATH="%SPARK_HOME%\python;%SPARK_HOME%\python\lib\py4j-0.10.9.5-src.zip;%PYTHONPATH%" (In users and systems variables)
	5-In Users and Systems PATH variables add this to Path "C:\spark\bin"
	
	
7- open Anaconda CMD prompt and cd  to c:\spark 
8- run "bin\pyspark --master local[3] --driver-memory 2g --packages com.crealytics:spark-excel_2.12:3.3.1_0.18.5"
it will create a file in users hidden directory ie "C:\Users\user_name\.ivy2\jars"
Copy all the jar files from this folder and paste in "C:\spark\jars"
9- Close Anaconda Navigator 
10- Open Anaconda Navigator and luanch notebook
11-  now the excell reading spark-excel will work.

Note: if does not work, re run step 8, and then open Anaconda Navigator and luanch notebook.
