:original_name: nosql_05_0050.html

.. _nosql_05_0050:

Scaling Up Storage Space of an Instance
=======================================

Function
--------

This API is used to scale up storage space of an instance.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/extend-volume

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

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | size            | Yes             | Integer         | Requested storage space. It must be an integer greater than the current storage space. |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | The maximum storage space depends on the engine type and specifications.               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

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

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/extend-volume

-  Scaling up storage space of an instance to 550 GB

   .. code-block::

      {
        "size" : 550
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
