:original_name: nosql_05_0051.html

.. _nosql_05_0051:

Adding Nodes for an Instance
============================

Function
--------

This API is used to add nodes for a specified instance.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/enlarge-node

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                               |
   +=================+=================+=================+===========================================================================================================================+
   | num             | Yes             | Integer         | Number of new nodes                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | No              | String          | ID of the subnet where the new node is deployed.                                                                          |
   |                 |                 |                 |                                                                                                                           |
   |                 |                 |                 | -  This parameter is transferred only when a new node is added to a GaussDB(for Cassandra) instance.                      |
   |                 |                 |                 | -  The transferred subnet ID must belong to the VPC where the current instance is deployed.                               |
   |                 |                 |                 | -  If this parameter is not transferred, the system will allocate a subnet with sufficient IP addresses for the new node. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID
   ========= ====== ===========

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/enlarge-node

-  Adding a node

   .. code-block::

      {
        "num" : 1
      }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "3711e2ad-5787-49bc-a47f-3f0b066af9f5"
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
