:original_name: nosql_05_0103.html

.. _nosql_05_0103:

Changing the Security Group of an Instance
==========================================

Function
--------

This API is used to change the security group associated with an instance.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

Abnormal instances do not support this operation.

Please confirm the modified security group rule. This policy may affect connections to the current instance, interrupting services.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/security-group

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

   ================= ========= ====== =============================
   Parameter         Mandatory Type   Description
   ================= ========= ====== =============================
   security_group_id Yes       String ID of the new security group.
   ================= ========= ====== =============================

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/security-group

-  Example request body

   .. code-block::

      {
        "security_group_id" : "73bed21a-708b-4985-b697-a96d0e0d2b39"
      }

Example Responses
-----------------

**Status code: 202**

No Content

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
