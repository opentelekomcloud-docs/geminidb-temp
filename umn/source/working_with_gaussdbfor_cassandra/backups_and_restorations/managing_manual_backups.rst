:original_name: nosql_03_0008.html

.. _nosql_03_0008:

Managing Manual Backups
=======================

To ensure data reliability, GaussDB(for Cassandra) allows you to manually back up DB instances whose status is **Available**. If a database or table is deleted, maliciously or accidentally, backups can help recover your data.

.. note::

   -  By default, you can create up to 50 backups.
   -  Manual backups are full backups.

Creating a Manual Backup
------------------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. Create a manual backup.

   **Method 1**

   On the **Instance Management** page, locate the DB instance you wish to back up and click **Create Backup** or **More** > **Create Backup** in the **Operation** column.

   **Method 2**

   a. On the **Instance Management** page, click the DB instance you wish to back up.
   b. On the **Backups & Restorations** page, click **Create Backup**.

   **Method 3**

   In the navigation pane on the left, choose **Backup Management**. On the displayed page, click **Create Backup**.

#. In the displayed dialog box, enter the backup name and description, and click **OK**.

   .. table:: **Table 1** Parameter description

      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                                                             |
      +==================+=========================================================================================================================================================================================+
      | DB Instance Name | The default value is the name of the DB instance to be backed up and cannot be modified.                                                                                                |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Backup Name      | The backup name must be 4 to 64 characters in length and start with a letter. Backup names are case-insensitive and can only contain letters, digits, hyphens (-), and underscores (_). |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description      | The description contains a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=                                                        |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. View the backup status after the task has been executed.

   -  During the creation of a manual backup, you can query the backup status on the **Backup Management** page or the **Backups & Restorations** page. The backup status is **Backing up**.
   -  If a manual backup was successfully created, the backup status is **Completed**.

Deleting a Manual Backup
------------------------

If you do not need the manual backup, you can delete it on the **Backup Management** page or the **Backups & Restorations** page.

Deleted backups are not displayed in the backup list.

.. important::

   The deletion operation is irreversible, so exercise caution when performing this operation.

**Method 1**

#. On the **Instance Management** page, click the DB instance whose backup you wish to delete.
#. On the **Backups & Restorations** page, locate the backup you wish to delete and click **Delete**.
#. In the **Delete Backup** dialog box, confirm the backup details and click **Yes**.

**Method 2**

#. On the **Backup Management** page, locate the target backup and click **Delete**.
#. In the **Delete Backup** dialog box, confirm the backup details and click **Yes**.
