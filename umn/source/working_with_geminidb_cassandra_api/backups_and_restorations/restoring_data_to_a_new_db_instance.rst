:original_name: nosql_03_0009.html

.. _nosql_03_0009:

Restoring Data to a New DB Instance
===================================

Scenarios
---------

GeminiDB Cassandra API allows you to restore the existing backup to a new DB instance.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. Restore a DB instance from the backup.

   **Method 1**

   a. On the **Instance Management** page, click the target DB instance.
   b. On the **Backups & Restorations** page, locate the target backup and click **Restore**.

   **Method 2**

   On the **Backup Management** page, locate the target backup and click **Restore**.

#. In the displayed dialog box, confirm the current instance details and restoration method and click **OK**.

   -  The default API type and DB engine version are the same as those of the original instance and cannot be changed.
   -  GeminiDB automatically calculates the minimum storage space required for restoration based on the size of the selected backup file. The storage space depends on the instance specifications, and must be a multiple of 10 GB.
   -  You need to set a new administrator password.

   -  To modify other parameters, see the description of creating DB instances of other DB engines in the *Getting Started*.

#. View the restoration results.

   A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

   After the restoration, the system will perform a full backup.

   The new DB instance is independent from the original one.
