## Spark Integrations

### Table of Contents

|Integrations                                                |
|------------------------------------------------------------|
|[Spark-MySQL Integration](#spark-mysql-integration)         |
|[Spark-MSSQL Integration](#spark-mssql-integration)         |
|[Spark-Cassandra Integration](#spark-cassandra-integration) |

### Spark-MySQL Integration
* Open Spark Shell 
```sh
spark-shell --packages mysql:mysql-connector-java:5.1.49
```
* Read the data from MySQL using Spark. By default MySQL run on port `3306`
```sh
val df = spark.read.format("jdbc")
.option("url","jdbc:mysql://localhost:3306/databasename")
.option("driver","com.mysql.jdbc.Driver")
.option("user","username")
.option("password","password")
.option("dbtable","tablename")
.load()
df.show()
```
* Write the data into MySQL using Spark
```sh
df.write.format("jdbc")
.option("url","jdbc:mysql://localhost:3306/database_name")
.option("driver","com.mysql.cj.jdbc.Driver")
.option("user","username")
.option("password","password")
.option("dbtable","target_tablename")
.save()

```
* In latest version of MySQL the driver name changed to `com.mysql.cj.jdbc.Driver`

**[⬆ Back to Top](#table-of-contents)**

### Spark-MSSQL Integration
* Open Spark Shell
```sh
spark-shell --packages com.microsoft.sqlserver:mssql-jdbc:12.2.0.jre8
```
* Read the data from MSSQL using Spark. By default MSSQL run on port `1433`
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
* Write the data into MSSQL using Spark
```sh
 df.write
  .format("jdbc")
  .option("url", "jdbc:sqlserver://hostname(or)ipaddress:port;databaseName=database_name")
  .option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
  .option("user","username")
  .option("password","password")
  .option("dbtable", "target_tableName")
  .save()
```
**[⬆ Back to Top](#table-of-contents)**

### Spark-Cassandra Integration
* Open Spark Shell
```sh
spark-shell --packages com.datastax.spark:spark-cassandra-connector_2.11:2.4.0
```
* Read the data from Cassandra using Spark. By default cassandra run on port `9042`
```sh
val df = spark.read
.format("org.apache.spark.sql.cassandra")
.option("spark.cassandra.connection.host","hostname")
.option("spark.cassandra.connection.port","9042")
.option("keyspace","Keyspacename")
.option("table","tablename")
.load()
			
df.show()
  ```
  * Write the data into Cassandra using Spark
  ```sh
  df.write
.format("org.apache.spark.sql.cassandra")
.option("spark.cassandra.connection.host","hostname")
.option("spark.cassandra.connection.port","9042")
.option("keyspace","keyspacename")
.option("table","target_tablename")
.save()
```
**[⬆ Back to Top](#table-of-contents)**

