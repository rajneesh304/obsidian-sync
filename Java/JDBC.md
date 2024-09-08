JDBC stands for Java Database Connectivity.

Steps to follow: 
1. Import packages
2. Load the Driver (provided by the databases; each DB will have its own driver)
3. Register the driver
4. Create a connection
5. Create a statement
6. Execute the statement
7. Close the connection

```java
String url = "jdbc:<oracle/postgresql>://<host>:<port>/<schema>"
Connection con = DriverManager.getConnection(url, username, password);


```