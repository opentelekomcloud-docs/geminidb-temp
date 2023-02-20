:original_name: nosql_03_0007.html

.. _nosql_03_0007:

Managing Automated Backups
==========================

GaussDB NoSQL creates automated backups to ensure data reliability. If a database or table is maliciously or accidentally deleted, backups can help you ensure you do not lose your data.

.. _nosql_03_0007__section7348925133816:

Automated Backup Policy
-----------------------

Automated backups are generated according to a backup policy and saved as packages in OBS buckets to ensure data confidentiality and durability. You are advised to regularly back up your database, in case it becomes faulty or damaged. However, backing up data might affect the database read and write performance so it is recommended that you enable automated backups during off-peak hours.

When you create a DB instance, an automated backup policy is enabled by default.

-  **Retention Period**: Automated backup files are saved for seven days by default. The backup retention period can range from 1 to 35 days.

   .. note::

      -  If the retention period is less than seven days, the system automatically backs up data every day.
      -  The system checks existing automated backup files and deletes the files that exceed the backup retention period you set.
      -  **Time Window**: An hour within 24 hours, such as 01:00-02:00 or 12:00-13:00. The backup time is in GMT format. If the DST or standard time is switched, the backup time segment changes with the time zone.

-  **Backup Cycle**: By default, each day of the week is selected.

   -  **All**: Each day of the week is selected. The system automatically backs up data every day.
   -  Select a cycle: You can select one or more days in a week. The system automatically backs up data at the specified time.

   .. note::

      A full backup starts within one hour of the time you specify. The amount of time required for the backup depends on the amount of data to be backed up. The more data has to be backed up, the longer it will take.

-  After a DB instance is created, you can modify the automated backup policy as needed. You can change the time window after the DB instance is created. The system backs up data based on the automated backup policy you have set.
-  If the automated backup policy is disabled, any automated backups in progress stop immediately.

Modifying an Automated Backup Policy
------------------------------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the DB instance you wish to modify the policy for.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. In the displayed dialog box, set the backup policy. Then, click **Yes** to save the configuration.

   For details about how to set a backup policy, see :ref:`Automated Backup Policy <nosql_03_0007__section7348925133816>`.

#. Check or manage the generated backups on the **Backup Management** page or on the **Backups & Restorations** page.

Disabling Automated Backup Policy
---------------------------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the DB instance you wish to modify the policy for.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**.

#. In the displayed dialog box, click |image1| to disable the backup policy and click **Yes**.

   When disabling the automated backup policy, you can decide whether to delete the automated backups by selecting **Delete automated backups**.

   -  If you select it, all backup files within the retention period will be deleted. No automated backups are displayed in the backup list until you enable the automated backup policy again.
   -  If you do not select it, all backup files within the retention period will be retained, but you can still manually delete them later if needed. For details, see section :ref:`Deleting an Automated Backup <nosql_03_0007__section106721241354>`.

   If the automated backup policy is disabled, any automated backups in progress stop immediately.

.. _nosql_03_0007__section106721241354:

Deleting an Automated Backup
----------------------------

If the automated backup policy is disabled, you can delete stored automated backups to free up storage space.

If the automated backup policy is enabled, the system will delete automated backups as they expire. You cannot delete them manually.

.. important::

   The deletion operation is irreversible, so exercise caution when performing this operation.

-  **Method 1**

   #. On the **Instance Management** page, click the DB instance you wish to delete backups for.
   #. On the **Backups & Restorations** page, locate the backup you wish to delete and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

-  **Method 2**

   #. On the **Backup Management** page, locate the target backup and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001158064793.png
