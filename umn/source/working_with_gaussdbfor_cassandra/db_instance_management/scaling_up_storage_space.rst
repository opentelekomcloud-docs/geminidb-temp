:original_name: nosql_increase_storage.html

.. _nosql_increase_storage:

Scaling Up Storage Space
========================

Scenarios
---------

This section describes how to scale up the storage space of a DB instance to suit your service requirements.

During the scale-up process, the DB instance will not restart, and your services will not be interrupted.

Precautions
-----------

Storage space can only be scaled up. It cannot be scaled down.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the DB instance you wish to scale up.

#. In the **Storage Space** area on the **Basic Information** page, click **Scale**.

#. On the displayed page, specify the new storage capacity and click **Next**.

   Select at least 1 GB each time you scale up the storage, and the storage size must be an integer.

#. On the displayed page, confirm the storage space.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to scale up the storage space.

#. Check the scale-up result.

   -  The status of the DB instance in the instance list is **Scaling up**.
   -  After the scale up is completed, the DB instance status becomes **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scale up was successful.
