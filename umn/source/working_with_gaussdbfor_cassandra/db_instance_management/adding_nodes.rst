:original_name: nosql_increase_nodes.html

.. _nosql_increase_nodes:

Adding Nodes
============

Scenarios
---------

This section describes how to add nodes to a DB instance to suit your service requirements. You can also delete a node as required. For details, see :ref:`Deleting Nodes <nosql_03_0004>`.

Precautions
-----------

-  Adding nodes may lead to the decrease of operations per second (OPS). You are advised to perform this operation during off-peak hours.
-  You can only add nodes when the instance status is **Available** or **Checking restoration**.
-  A DB instance cannot be deleted when one or more nodes are being added.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click the DB instance you wish to add nodes for.
#. In the **Node Information** area on the **Basic Information** page, click **Add Node**.
#. Specify **Add Nodes** and click **Next**.

   -  By default, the specifications of new nodes are the same as the DB instance and cannot be modified.
   -  Up to 200 nodes can be added to a GaussDB(for Cassandra) instance.

#. On the displayed page, confirm the node configuration details.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to add the nodes.

#. View the result of adding nodes.

   -  The status of the DB instance in the instance list is **Adding node**.
   -  After the nodes are added, the DB instance status becomes **Available**.
   -  Click the DB instance name. In the **Node Information** area on the **Basic Information** page, view the information about the new nodes.
