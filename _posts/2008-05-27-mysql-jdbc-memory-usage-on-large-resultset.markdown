---
author: benjchristensen
comments: true
date: 2008-05-27 21:23:20+00:00
layout: post
slug: mysql-jdbc-memory-usage-on-large-resultset
title: MySQL JDBC Memory Usage on Large ResultSet
wordpress_id: 59
categories:
- Code
- Performance
---

I recently came across the problem of large resultsets being pulled into a java app via MySQL JDBC. I had dealt with this years ago but forgotten about it.

The test case below shows how the entire ResultSet is buffered in memory by default -- which can be a "very bad thing" when dealing with hundreds or thousands of megabytes of data when it's intended to be processed row by row.

**Using mysql-connector-java-3.1.12-bin.jar and a JDK 5 with 32MB heap:**


ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 1  Free: 32




Retrieving data ...




Ran out of memory at row: 0




java.lang.OutOfMemoryError: Java heap space




at com.mysql.jdbc.ByteArrayBuffer.getBytes(ByteArrayBuffer.java:128)




at com.mysql.jdbc.ByteArrayBuffer.readLenByteArray(ByteArrayBuffer.java:248)




at com.mysql.jdbc.MysqlIO.nextRow(MysqlIO.java:1304)




at com.mysql.jdbc.MysqlIO.readSingleRowSet(MysqlIO.java:2272)




at com.mysql.jdbc.MysqlIO.getResultSet(MysqlIO.java:423)




at com.mysql.jdbc.MysqlIO.readResultsForQueryOrUpdate(MysqlIO.java:1962)




at com.mysql.jdbc.MysqlIO.readAllResults(MysqlIO.java:1385)




at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:1728)




at com.mysql.jdbc.Connection.execSQL(Connection.java:2988)




at com.mysql.jdbc.Connection.execSQL(Connection.java:2917)




at com.mysql.jdbc.Statement.executeQuery(Statement.java:824)




at JDBCTest.main(JDBCTest.java:26)


 

**Using mysql-connector-java-5.1.6-bin.jar and the same JDK 5 with 32MB heap:**


ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 1  Free: 32




Retrieving data ...




Ran out of memory at row: 0




java.lang.OutOfMemoryError: Java heap space




at com.mysql.jdbc.ByteArrayBuffer.getBytes(ByteArrayBuffer.java:128)




at com.mysql.jdbc.ByteArrayBuffer.readLenByteArray(ByteArrayBuffer.java:248)




at com.mysql.jdbc.MysqlIO.nextRow(MysqlIO.java:1304)




at com.mysql.jdbc.MysqlIO.readSingleRowSet(MysqlIO.java:2272)




at com.mysql.jdbc.MysqlIO.getResultSet(MysqlIO.java:423)




at com.mysql.jdbc.MysqlIO.readResultsForQueryOrUpdate(MysqlIO.java:1962)




at com.mysql.jdbc.MysqlIO.readAllResults(MysqlIO.java:1385)




at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:1728)




at com.mysql.jdbc.Connection.execSQL(Connection.java:2988)




at com.mysql.jdbc.Connection.execSQL(Connection.java:2917)




at com.mysql.jdbc.Statement.executeQuery(Statement.java:824)




at JDBCTest.main(JDBCTest.java:26)


 

Thus we see that both the old and new versions of the MySQL JDBC driver by default attempt to load the entire resultset into memory.

 

I now increase the heap to 1GB to allow it to grow and find that the test query uses up > 500MB of heap before it even starts the rs.next() loop.


ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 1  Free: 32




Retrieving data ...




ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 298  Used: 183  Free: 115




ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 527  Used: 381  Free: 146




Starting to retrieve data. Memory Used: 517




Done retrieving data => 2318284   Memory Used: 551


 

Here is the code for this:

 

            ResultSet rs = conn.createStatement().executeQuery("<sql query that returns lots of data>");

            System.out.println("Starting to retrieve data. Memory Used: " + getUsedMemory());

            while (rs.next()) {

                rs.getString(1);

                rowsReturned++;

            }

            System.out.println("Done retrieving data => " + rowsReturned + "   Memory Used: "  

+ getUsedMemory());

 

Thus you can see that the "executeQuery()" method loads up 500MB of data before it passes on the "rs.next()" loop. The full ResultSet is being buffered in memory.

 

**Solution**

To make the JDBC driver stream the results instead of buffer them all first we do the following:

            stmt.setFetchSize(Integer.MIN_VALUE);


Then we get this result instead:







ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 1  Free: 32




Retrieving data ...




Starting to retrieve data. Memory Used: 2




ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 1  Free: 32




ET-COMMONS INFO: JVM MEMORY MONITOR => Total: 33  Used: 2  Free: 31




Done retrieving data => 2318284   Memory Used: 2






 

Now it behaves like we expect it to ... only 2MB used instead of > 500MB.

 

There are some caveats:



	
  * http://javaquirks.blogspot.com/2007/12/mysql-streaming-result-set.html

	
  * http://dev.mysql.com/doc/refman/5.0/en/connector-j-reference-implementation-notes.html




In the second link of official documentation we read (emphasis in red added by myself):




----------------------------------------------------------------------






**ResultSet**

By default, ResultSets are completely retrieved and stored in memory. In most cases this is the most efficient way to operate, and due to the design of the MySQL network protocol is easier to implement. If you are working with ResultSets that have a large number of rows or large values, and can not allocate heap space in your JVM for the memory required, you can tell the driver to stream the results back one row at a time.

To enable this functionality, you need to create a Statement instance in the following manner:

    
    stmt = conn.createStatement(java.sql.ResultSet.TYPE_FORWARD_ONLY,
                  java.sql.ResultSet.CONCUR_READ_ONLY);
    stmt.setFetchSize(Integer.MIN_VALUE);


The combination of a forward-only, read-only result set, with a fetch size of `Integer.MIN_VALUE` serves as a signal to the driver to stream result sets row-by-row. After this any result sets created with the statement will be retrieved row-by-row.

There are some caveats with this approach. You will have to read all of the rows in the result set (or close it) before you can issue any other queries on the connection, or an exception will be thrown.

The earliest the locks these statements hold can be released (whether they be `MyISAM` table-level locks or row-level locks in some other storage engine such as `InnoDB`) is when the statement completes.

If the statement is within scope of a transaction, then locks are released when the transaction completes (which implies that the statement needs to complete first). As with most other databases, statements are not complete until all the results pending on the statement are read or the active result set for the statement is closed.

Therefore, if using streaming results, you should process them as quickly as possible if you want to maintain concurrent access to the tables referenced by the statement producing the result set.




 

 
