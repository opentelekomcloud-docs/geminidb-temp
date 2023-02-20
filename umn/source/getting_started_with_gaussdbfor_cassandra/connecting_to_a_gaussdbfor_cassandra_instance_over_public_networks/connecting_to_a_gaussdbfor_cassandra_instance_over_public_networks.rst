:original_name: nosql_02_0009.html

.. _nosql_02_0009:

Connecting to a GaussDB(for Cassandra) Instance Over Public Networks
====================================================================

Scenarios
---------

You can use an ECS or local device to connect to a GaussDB NoSQL instance over a public network.

This section describes how to use a Linux ECS to connect to a GaussDB(for Cassandra) instance over a public network.

Prerequisites
-------------

-  Bind an EIP to the GaussDB(for Cassandra) instance node and set security group rules.
-  Create an ECS running Linux. For details, see "Creating ECSs" in *ECS User Guide*.
-  Obtain the Cassandra client installation package from the Cassandra official website.

Connecting to a DB Instance Through a Cassandra Client
------------------------------------------------------

#. Log in to the ECS. For details, see the section "Logging In to an ECS" in the *Elastic Cloud Server User Guide*.

#. Upload the Cassandra client installation package to ECS.

#. Obtain the client tool cqlsh.

#. Connect to the DB instance in the directory where the cqlsh tool is located.

   **cqlsh** <*DB_HOST*> <*DB_PORT*> **-u** <*DB_USER*>

   Example:

   **cqlsh 192.168.1.8 8635 -u rwuser**

   .. note::

      -  *<DB_HOST>* indicates the EIP of the node to be connected. Obtain the value from the **EIP** column in the node list on the **Basic Information** page.
      -  *<DB_PORT>* indicates the port number. The default value is **8635** and cannot be changed.
      -  *<DB_USER>* indicates the database account name. The default value is **rwuser**.

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      rwuser@cqlsh>

**Follow-up Operations**
------------------------

After logging in to the GaussDB(for Cassandra) instance, you can perform the following operations:

-  Run the **HELP** command to view all supported commands.

-  **HELP** *<COMMAND>*: This command queries the usage of a command. Example: **HELP DESC**
-  Keyspace syntax

   -  Create a keyspace. Example:

      **CREATE KEYSPACE IF NOT EXISTS nosql WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '3'};**

      Set the keyspace name to **nosql**, **replication** to **SimpleStrategy**, and number of replicas to **3**.

   -  **DESC** *<keyspace_name>*: This command verifies the creation result.

   -  **use** *<keyspace_name>*: This command switches to the keyspace you created.

   -  **DROP** **KEYSPACE** *<keyspace_name>*: This command deletes the keyspace you created.

-  Table syntax

   -  Create a table. Example:

      **CREATE TABLE nosql_table(user_id int, age int, user_name text, PRIMARY KEY(user_id));**

      The table name is **nosql_table**, and the following three columns are defined: **user_id**, **age**, and **user_name**. **user_id** is of the int type and indicates the user ID. **age** is of the int type and indicates the age of a user. **user_name** is of the text type and indicates the user name. The primary key is **user_id**.

   -  **DESC** *<table_name>*: This command verifies the creation result.

   -  Insert data into the table. Example:

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (1, 10, 'user1');**

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (2, 20, 'user2');**

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (3, 30, 'user3');**

   -  **SELECT \* FROM** *<table_name>*: This command queries table data.

   -  Add a column to the table. Example

      **ALTER TABLE nosql_table ADD gender text;**

   -  Insert data to the added column. Example:

      **UPDATE nosql.nosql_table SET prename = 'user_prename1' WHERE user_id = 1;**

      **UPDATE nosql.nosql_table SET prename = 'user_prename2' WHERE user_id = 2;**

      **UPDATE nosql.nosql_table SET prename = 'user_prename3' WHERE user_id = 3;**

   -  Delete data in a keyspace. Example:

      Delete the age data of the user whose ID is **1**.

      **DELETE age FROM nosql.nosql_table WHERE user_id=1;**

      Delete the entire record of the user whose ID is **2**.

      **DELETE FROM nosql.nosql_table WHERE user_id=2;**

   -  Clear all records in the table. Example:

      **TRUNCATE nosql.nosql_table;**

   -  Delete the entire table. Example:

      **DROP TABLE nosql.nosql_table;**
