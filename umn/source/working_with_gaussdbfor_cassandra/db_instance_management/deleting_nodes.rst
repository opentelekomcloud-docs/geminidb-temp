:original_name: nosql_03_0004.html

.. _nosql_03_0004:

Deleting Nodes
==============

Scenarios
---------

You can delete nodes that are no longer used to release resources.

Precautions
-----------

Deleted nodes cannot be recovered. Exercise caution when performing this operation.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click the DB instance whose nodes you wish to delete.
#. In the **Node Information** area on the **Basic Information** page, locate the node you wish to delete and click **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.

   -  The status of the DB instance in the instance list is **Deleting node**.
   -  After the deletion, the DB instance status becomes **Available**.
