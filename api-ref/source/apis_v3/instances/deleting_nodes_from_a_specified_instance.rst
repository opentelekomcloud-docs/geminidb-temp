:original_name: nosql_05_0052.html

.. _nosql_05_0052:

Deleting Nodes from a Specified Instance
========================================

Function
--------

This API is used to delete nodes from a specified instance.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/reduce-node

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                  |
   +=================+=================+==================+==============================================================================================================================================================================================+
   | num             | No              | Integer          | Number of nodes to be deleted randomly.                                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  | For GeminiDB Cassandra instances, the value ranges from **1** to **10**.                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  | .. note::                                                                                                                                                                                    |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  |    If users connect to nodes using the client, do no choose to delete node randomly.                                                                                                         |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_list       | No              | Array of strings | ID of the node to be deleted. Make sure that the node can be deleted. If this parameter is not transferred, the number of nodes to be deleted is based on the internal policy of the system. |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  | .. note::                                                                                                                                                                                    |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  |    -  Either **num** or **node_list** must be set.                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  |       -  If **node_list** is transferred, its value can contain 1 to 10 characters for GeminiDB Cassandra.                                                                                   |
   |                 |                 |                  |       -  If **num** and **node_list** are both transferred, the value of **node_list** takes effect.                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                              |
   |                 |                 |                  |    -  If **node_list** is empty, instance nodes are deleted randomly. If **node_list** is not empty, only the node whose ID is specified is deleted.                                         |
   |                 |                 |                  |    -  Before a node is deleted, do not connect to the node directly to avoid service interruptions.                                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   +-----------+--------+---------------------------------------------------------------------+
   | Parameter | Type   | Description                                                         |
   +===========+========+=====================================================================+
   | job_id    | String | Task ID. This parameter is returned only for pay-per-use instances. |
   +-----------+--------+---------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/reduce-node

-  Deleting a node

   .. code-block::

      {
         "num" : 1,
         "node_list" : [ "116ba14da34a42d28ecd83a38c218907no12" ]
      }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "04efe8e2-9255-44ae-a98b-d87cae411890"
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
