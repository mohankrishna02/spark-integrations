## Spark Integrations

### Table of Contents

|Integrations                                           |
|-------------------------------------------------------|
|[Spark-MySQL Integration](#spark-mysql-integration)    |
|[Spark-MSSQL Integration](#spark-mssql-integration)    |

### Spark-MySQL Integration
* Open Spark Shell 
```sh
spark-shell --packages mysql:mysql-connector-java:5.1.49
```
* Read the data from MySQL using Spark
```sh
val df = spark.read.format("jdbc").option("url","jdbc:mysql://localhost/practice").option("driver","com.mysql.jdbc.Driver").option("user","root").option("password","cloudera").option("dbtable","places").load()
df.show()
```
* In latest version of MySQL the driver name changed to `com.mysql.cj.jdbc.Driver`

**[⬆ Back to Top](#table-of-contents)**

### Spark-MSSQL Integration
* Open Spark Shell
```sh
spark-shell --packages com.microsoft.sqlserver:mssql-jdbc:12.2.0.jre8
```
* Read the data from MySQL using Spark
```sh
val df = spark.read
  .format("jdbc")
  .option("url", "jdbc:sqlserver://hostname(or)ipaddress:port;databaseName=database_name")
  .option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
  .option("user","username")
  .option("password","password")
  .option("dbtable", "tableName")
  .load()
df.show()
```


