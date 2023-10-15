:original_name: nosql_05_0102.html

.. _nosql_05_0102:

Editing the Name of an Instance
===============================

Function
--------

This API is used to edit the name of an instance.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

The name of the instance that is being created or fails to be created cannot be edited.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/name

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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================+
   | name            | Yes             | String          | New instance name.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | The name:                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | Must start with a letter and can include 4 to 64 characters. It is case-sensitive and can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/name

-  Changing the instance name to **myNewName**

   .. code-block::

      {
        "name" : "myNewName"
      }

Example Responses
-----------------

None

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
