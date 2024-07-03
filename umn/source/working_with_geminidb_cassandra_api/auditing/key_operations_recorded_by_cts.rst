:original_name: nosql_03_0017.html

.. _nosql_03_0017:

Key Operations Recorded by CTS
==============================

With CTS, you can record operations associated with GeminiDB for later query, audit, and backtrack operations.

:ref:`Table 1 <nosql_03_0017__en-us_topic_0108439405_table7128270172415>` lists the key operations that can be recorded by CTS.

.. _nosql_03_0017__en-us_topic_0108439405_table7128270172415:

.. table:: **Table 1** GeminiDB Cassandra key operations

   +------------------------------------+----------------+-----------------------------------+
   | Operation                          | Resource       | Trace Name                        |
   +====================================+================+===================================+
   | Creating a DB instance             | instance       | NoSQLCreateInstance               |
   +------------------------------------+----------------+-----------------------------------+
   | Deleting a DB instance             | instance       | NoSQLDeleteInstance               |
   +------------------------------------+----------------+-----------------------------------+
   | Adding nodes                       | instance       | NoSQLEnlargeInstance              |
   +------------------------------------+----------------+-----------------------------------+
   | Deleting nodes                     | instance       | NoSQLReduceInstance               |
   +------------------------------------+----------------+-----------------------------------+
   | Restarting a DB instance           | instance       | NoSQLRestartInstance              |
   +------------------------------------+----------------+-----------------------------------+
   | Restoring data to new DB instances | instance       | NoSQLRestoreNewInstance           |
   +------------------------------------+----------------+-----------------------------------+
   | Scaling up storage space           | instance       | NoSQLExtendInstanceVolume         |
   +------------------------------------+----------------+-----------------------------------+
   | Resetting a password               | instance       | NoSQLResetPassword                |
   +------------------------------------+----------------+-----------------------------------+
   | Changing DB instance names         | instance       | NoSQLRenameInstance               |
   +------------------------------------+----------------+-----------------------------------+
   | Changing a DB instance class       | instance       | NoSQLResizeInstance               |
   +------------------------------------+----------------+-----------------------------------+
   | Binding an EIP                     | instance       | NoSQLBindEIP                      |
   +------------------------------------+----------------+-----------------------------------+
   | Unbinding an EIP                   | instance       | NoSQLUnBindEIP                    |
   +------------------------------------+----------------+-----------------------------------+
   | Creating a backup                  | backup         | NoSQLCreateBackup                 |
   +------------------------------------+----------------+-----------------------------------+
   | Deleting a backup                  | backup         | NoSQLDeleteBackup                 |
   +------------------------------------+----------------+-----------------------------------+
   | Setting a backup policy            | backup         | NoSQLSetBackupPolicy              |
   +------------------------------------+----------------+-----------------------------------+
   | Adding an instance tag             | tag            | NoSQLAddTags                      |
   +------------------------------------+----------------+-----------------------------------+
   | Modifying an instance tag          | tag            | NoSQLModifyInstanceTag            |
   +------------------------------------+----------------+-----------------------------------+
   | Deleting an instance tag           | tag            | NoSQLDeleteInstanceTag            |
   +------------------------------------+----------------+-----------------------------------+
   | Creating a parameter template      | parameterGroup | NoSQLCreateConfigurations         |
   +------------------------------------+----------------+-----------------------------------+
   | Modifying a parameter template     | parameterGroup | NoSQLUpdateConfigurations         |
   +------------------------------------+----------------+-----------------------------------+
   | Modifying instance parameters      | parameterGroup | NoSQLUpdateInstanceConfigurations |
   +------------------------------------+----------------+-----------------------------------+
   | Replicating a parameter template   | parameterGroup | NoSQLCopyConfigurations           |
   +------------------------------------+----------------+-----------------------------------+
   | Resetting a parameter template     | parameterGroup | NoSQLResetConfigurations          |
   +------------------------------------+----------------+-----------------------------------+
   | Applying a parameter template      | parameterGroup | NoSQLApplyConfigurations          |
   +------------------------------------+----------------+-----------------------------------+
   | Deleting a parameter template      | parameterGroup | NoSQLDeleteConfigurations         |
   +------------------------------------+----------------+-----------------------------------+
