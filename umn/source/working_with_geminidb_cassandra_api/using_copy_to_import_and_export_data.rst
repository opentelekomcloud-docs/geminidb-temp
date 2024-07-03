:original_name: nosql_03_0015.html

.. _nosql_03_0015:

Using COPY to Import and Export Data
====================================

Scenarios
---------

The **COPY** command is one of cqlsh commands. It includes **COPY TO** and **COPY FROM**. They are used to copy data to and from Cassandra.

You can run the **COPY TO** command to export data from an existing Cassandra instance and then run the **COPY FROM** command to import the data to an RDBMS instance or a new Cassandra instance. Currently, you can copy data to or from the CSV and JSON files.

Precautions
-----------

You are advised to import and export data during off-peak hours to avoid the impact on your services.

Prerequisites
-------------

You have connected to a DB instance. For details, see :ref:`Connecting to a GeminiDB Cassandra Instance Over Private Networks <nosql_02_0006>`.

Method
------

-  Start cqlsh, and then run the **COPY** command.

   **./cqlsh** <*DB_HOST*> **-u** *<user_name>*

   **COPY cycling.cyclist_name TO '/home/cas/copydata';**

   .. note::

      -  *<DB_HOST>* indicates the IP address and port of the native Cassandra database. Change it based on the site requirements.
      -  **-e**: Executes a specified statement in the background, then exits.
      -  **cycling.cyclist_name**: indicates the database name and table name. Change it based on the site requirements.

-  If there is large amount of data, add the **-e** parameter in the command to perform operations in the background.

   **./cqlsh** <*DB_HOST*> **-u** *<user_name>* **-e "COPY** *cycling.cyclist_name* **TO '/home/cas/copydata'";**

   .. note::

      -  <*DB_HOST*> indicates the IP address and port of the native Cassandra database. Change it based on the site requirements.
      -  **-e**: Executes a specified statement in the background, then exits.
      -  **cycling.cyclist_name**: indicates the database name and table name. Change it based on the site requirements.

COPY TO
-------

-  Command format:

   **COPY** *<table name>* **[(**\ *<column>*\ **, ...)] TO** *<file name>* **WITH** *<copy option>* **[AND** *<copy option>* **...]**

-  Example:

   **nohup ./cqlsh** <*DB_HOST*> **--request-timeout=3600 --debug -e "COPY nihao.sz_user TO '/home/cas/copydata' with WHERECONDITION='update_timestamp=1' NUMPROCESSES=12 AND RATEFILE='rate.txt' AND RESULTFILE='export_result' AND dataformats='json';" >export.log 2>&1 &**

Parameter description:

The common parameters are as follows: **NUMPROCESSES**, **RATEFILE**, **PAGESIZE**, **BEGINTOKEN**, **ENDTOKEN**, **MAXATTEMPTS**, and **MAXOUTPUTSIZE**.

The newly added parameters are as follows: **RESULTFILE**, **DATAFORMATS**, and **WHERECONDITION**.

For details about other COPY TO parameters, see the `Cassandra official documentation <https://cassandra.apache.org/doc/latest/tools/cqlsh.html#copy-to>`__.

-  **file name**: specifies the directory or file the data is copied to. The data is exported to a file by default.

   -  If you specify an existing directory to export the file, the system exports data to different files in the directory based on the specified range. If no data is exported for a given range, no file is generated.

      **./cqlsh** <*DB_HOST*> **-e "COPY** *cycling.cyclist_name* **TO '/home/cas/copydata'"**

   -  When you specify a file name, data is exported to the file. If the file does not exist, the system automatically creates a file as you named it.

      **./cqlsh** <*DB_HOST*> **-e "COPY** *cycling.cyclist_name* **TO '/home/cas/copydata/cycling.cyclist_name'"**

-  **NUMPROCESSES** is the number of exported threads. The range is divided by the number of threads. The more threads are exported, the smaller the ranges are. If the number of threads is too large, the server may be overloaded and the export may fail. You should select a suitable number of threads for export.

   The default number of threads is calculated as follows: **<Number of vCPUs>-1**

-  **RATEFILE** is the rate file. After the file path is specified, the instantaneous rate of the export process is displayed for evaluating the export performance.

-  **PAGESIZE** is the number of rows queried in a single page. The default value is **1000**. Do not set this parameter to a small value, or the export performance will suffer.

-  **BEGINTOKEN** and **ENDTOKEN** are the range to be exported. By default, all data is exported.

-  **MAXATTEMPTS** is the number of retries for each query. If the maximum number of retries of a query is reached, the export fails.

-  **MAXOUTPUTSIZE** is the maximum number of rows in an exported file. If the number of exported rows is greater than the value, another file is generated. By default, the number of rows is not limited.

   **./cqlsh** <*DB_HOST*> **-e "COPY** *cycling.cyclist_name* **TO '/home/cas/copydata/cycling.cyclist_name' with MAXOUTPUTSIZE=1"**

-  **RESULTFILE** is the path of the result file. If this parameter is not set, the result file is generated in the current directory by default. If there is already a result file in the directory, the file will be renamed. The exported results show the following information: whether the export is successful, total number of exported rows and rate, number of exported ranges, number of successful or failed ranges, and number of exported rows in each range.

-  **DATAFORMATS** is the data format to be exported. The value can be **csv** or **json**. The default value is **csv**. If the value is in set to **json**, data will be exported in JSON format.

-  **WHERECONDITION** is the query criteria to be exported. The query criteria can be exported. For non-primary-key columns, the export performance can be improved if the query is based on indexes.

   -  Supported operators: >=, <=, >, <, and =
   -  If the value contains special characters, for example, ",><=', add double quotation marks to the value.

COPY FROM
---------

-  Command format:

   **COPY** *<table name>* **[(**\ *<column>*\ **, ...)] FROM** *<file name>* **WITH** *<copy option>* **[AND** *<copy option>* **...]**

-  Example:

   **nohup ./cqlsh** <*DB_HOST*> **--request-timeout=3600 --debug -e "COPY nihao.sz_user FROM '/home/cas/copydata' with NUMPROCESSES=12 AND RATEFILE='rate.txt' AND dataformats='json';" >import.log 2>&1 &**

Parameter description:

The common parameters are as follows: **NUMPROCESSES**, **MAXROWS**, **INGESTRATE**, **ERRFILE**, **MAXBATCHSIZE**, **MINBATCHSIZE**, **CHUNKSIZE**, **MAXPARSEERRORS**, **MAXINSERTERRORS**, **SKIPROWS**, and **SKIPCOLS**.

The newly added parameter is **DATAFORMATS**.

For details about other COPY FROM parameters, see the `Cassandra official documentation <http://cassandra.apache.org/doc/latest/tools/cqlsh.html#copy-from>`__.

-  **file name** is the path the file will be imported to. The value can be a directory, a file, or a list of file names separated by commas (,). If the value is set to a specified directory, all files in the directory are imported.
-  **NUMPROCESSES** is the number of imported threads.
-  **MAXROWS** is the maximum number of rows to be imported. By default, the number of rows is not limited.
-  **INGESTRATE** is the maximum number of rows to be imported per second. The default value is **100000**.
-  **ERRFILE**: The columns that fail to be imported are stored in this file.
-  **MAXBATCHSIZE** is the maximum number of rows to be imported in each batch. The default value is **20**.
-  **MINBATCHSIZE** is the minimum number of rows to be imported in each batch. The default value is **2**.
-  **CHUNKSIZE** is the number of rows that the main thread transfers to a child thread each time. The default value is **1000**.
-  **MAXPARSEERRORS**: indicates the maximum number of rows whose syntax parsing errors can be ignored. By default, the number of rows is not limited.
-  **MAXINSERTERRORS**: indicates the maximum number of rows that can be ignored when the rows fail to be inserted. The default value is **1000**.
-  **SKIPROWS** is the number of rows that are skipped during the import. The default value is **0**, meaning that no row is skipped.
-  **SKIPCOLS** is the names of the columns that are ignored during the import. The column names are separated by commas (,). The value is not ignored by default.
-  **DATAFORMATS** is the data format to be imported. The value can be **csv** or **json**. The default value is **csv**. If the data is in JSON format, set this value to **json**.
