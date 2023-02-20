:original_name: nosql_03_0026.html

.. _nosql_03_0026:

Changing a DB Instance Class
============================

Scenarios
---------

This section describes how to change the CPU or memory of your instance to suit your service requirements.

Precautions
-----------

-  Instances can be scaled up or down.
-  Services will be interrupted for 5 to 10 minutes when you change DB instance CPU or memory, so you are advised to perform these operations during off-peak hours.
-  You are not advised to perform DDL operations when changing the CPU and memory.

   .. note::

      A data definition language (DDL) is a syntax for defining data structures and database objects. Common examples of DDL statements include CREATE, ALTER, and DROP. DDL is used to create, modify, and delete database objects, such as tables, indexes, views, functions, stored procedures, and triggers.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the DB instance you wish to change the CPU and memory for.

#. In the in **DB Information** area on the **Basic Information** page, click **Change** next to the **Instance Class** field.

#. On the displayed page, select the desired vCPUs and memory and click **Next**.

#. On the displayed page, confirm the instance class.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to change the instance class.

#. View the DB instance class change result.

   Go to the **Basic Information** page and in the **DB Information** area you can see the new instance class.

Method 2
--------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, locate the instance you want to change the class for and choose **More** > **Change Instance Class** in the **Operation** column.

#. On the displayed page, select the desired vCPUs and memory and click **Next**.

#. On the displayed page, confirm the instance class.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to change the instance class.

#. View the DB instance class change result.

   Go to the **Basic Information** page and in the **DB Information** area you can see the new instance class.
