# Azure SQL

## Deploy Azure SQL Database for free

https://learn.microsoft.com/en-us/azure/azure-sql/database/free-offer?view=azuresql

## Provision an Azure SQL database to store application data

https://learn.microsoft.com/en-us/training/modules/provision-azure-sql-db/?source=recommendations


## Introduction to SQL Server on Linux

Why use SQL Server on Linux?

If you want to run SQL Server, remember that you're not limited to the Windows platform. Because Linux is open source, you can install it on low-cost commodity hardware, reducing the operating system licensing expense. Linux also has a smaller footprint and lower hardware requirements, which make it faster to spin up Linux-based VMs over Windows-based servers.
SQL Server on Linux supports Ubuntu, Red Hat Enterprise Linux, and SUSE.


Containers

You can run SQL Server in Linux containers.


SQL Server on Linux features

* Performance
* In-Memory Online Transaction Processing (OLTP)
* Columnstore index
* Query Store

```sql

-- Your DBA team completes a monthly performance tuning task to ensure the correct query plans are used.
-- The team also reports on the top 10 longest-running queries to the development lead and checks on any resource locks. The Query Store supports all these tasks, and you can enable it with Transact-SQL:

ALTER DATABASE <database name>
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);

```

Automatic Tuning and Intelligent Query Processing

You can enable automatic plan choice correction after the Query Store is enabled. With Automatic Tuning enabled, SQL Server monitors query performance. If a new query plan does worse than the previous version, it can replace the new plan with the better performing previous version. The option is available at the database level with an ALTER statement:



```sql
ALTER DATABASE <database name>
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON );
```

Security

* Transparent Data Encryption (TDE) encrypts data-at-rest when it's stored in database files. 
* Always Encrypted ensures that only users who own data can view and process it
* Auditing, Row-level security, dynamic data masking, data discovery and classification


SQL Server Agent

* Transact-SQL jobs
* DB mail
* Log shipping

By default, SQL Server Agent is disabled, but it's installed and can be enabled using the command-line mssql-conf utility.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl restart mssql-server

```
High availability

PolyBase

Example:

Suppose you have data in SQL Server that records sales for your product catalog, but the data that records how much it costs to make your products is in an SAP HANA database.

* Use an Extract, Transform, Load (ETL) package to migrate data from one database system to the other.
* Query both databases and then write some custom code to join and integrate the results into a single report.
* With PolyBase, you can create an external table in SQL Server. An external table is a connection to an external system and a dataset hosted there. Once created, clients can submit queries to the external table in exactly the same way they would to internal tables.


!Note

On Linux operating systems, PolyBase is supported in SQL Server 2019 or later. To use it, you must install the mssql-server-polybase package, in addition to SQL Server 2019.

Machine Learning Services, Graph support, Full-text search, , ETL workloads (SQL Server Integration Services (SSIS) packages.


Tools for SQL Server on Linux

When an organization runs SQL Server on Windows servers, the principal administration tool is SQL Server Management Studio (SSMS). This tool doesn't run on Linux, although you can connect it to a Linux SQL Server from Windows computer.

Native Linux tools

* Software installation and upgrades are done using apt [...],
* After SQL Server is installed, it runs as a Linux service, so you can use systemd to start, stop, or restart the database server.


SQL Server administration tools

* Remember that, if you have a Windows computer with SSMS installed on it, you can connect it to SQL Servers that run on Linux and administer them as you would any other SQL Server. 

Azure Data Studio

* Azure Data Studio is a free, graphical, cross-platform SQL Server administration and development application that runs on Linux, Windows, or Mac. 
* functionality is limited

SQL Server command-line tools


* Microsoft provides a set of command-line tools you can use to administer and develop databases on SQL Server on Linux.
* mssql-cli provides Transact-SQL IntelliSense syntax highlighting, formatted query results, and a multi-line edit mode.
* mssql-conf is a set of scripts that you run after installation, and later, to configure SQL Server on Linux. For example, you use these scripts to enable SQL Server Agent, or set up a High Availability Group.
* mssql-tools is a package that contains sqlcmd and bcp commands, which have the same functions as on Windows.


Use containers with SQL Server on Linux

Reasons to use Virtual Machines

* With VMs, you host a Linux machine on Windows, or a Windows machine on macOS, giving greater flexibility. VMs allow you to host multiple applications with tight integration in a single VM. Containers traditionally only host single applications.

Reasons to use containers

* You only need to patch and update a single OS, rather than every guest OS on each VM. The containers are smaller and more straightforward, so they can be started in seconds rather than the minutes it takes to start a VM.

Containerized SQL Server on Linux

* One problem with databases running in containers is persistent storage. You must provide a storage location outside the container where the database can keep database files. Changes are then available to all containers in a cluster.



https://learn.microsoft.com/en-us/training/modules/introduction-sql-server-linux/

