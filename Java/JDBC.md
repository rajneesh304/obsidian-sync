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
Statement st = con.createStatement();
ResultSet rs = st.executeQuery(sql);
rs.next();
String name = rs.getString(1);
```

| Statement                                              | PreparedStatement                                             |
| ------------------------------------------------------ | ------------------------------------------------------------- |
| It is used when SQL query is to be executed only once. | It is used when SQL query is to be executed multiple times.   |
| You can not pass parameters at runtime.                | You can pass parameters at runtime.                           |
| Used for CREATE, ALTER, DROP statements.               | Used for the queries which are to be executed multiple times. |
| Performance is very low.                               | Performance is better than Statement.                         |
| It is base interface.                                  | It extends statement interface.                               |
| Used to execute normal SQL queries.                    | Used to execute dynamic SQL queries.                          |
| We can not use statement for reading binary data.      | We can use Preparedstatement for reading binary data.         |
| It is used for DDL statements.                         | It is used for any SQL Query.                                 |
| We can not use statement for writing binary data.      | We can use Preparedstatement for writing binary data.         |
| No binary protocol is used for communication.          | Binary protocol is used for communication.                    |