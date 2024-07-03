:original_name: nosql_03_0003.html

.. _nosql_03_0003:

Restarting a DB Instance
========================

Scenarios
---------

You may need to occasionally restart a DB instance to perform routine maintenance.

Precautions
-----------

-  If the instance status is **Available**, **Abnormal**, or **Checking restoration**, you can restart the instance.
-  Restarting a DB instance interrupts services, so exercise caution when performing this operation.
-  If you restart a DB instance, all nodes in the instance are also restarted.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instance Management** page, locate the DB instance you wish to restart and choose **More** > **Restart** in the **Operation** column.

   Alternatively, click the DB instance you wish to restart, and on the displayed **Basic Information** page, click **Restart** in the upper right corner of the page.

#. In the displayed dialog box, click **Yes**.
