:original_name: ListInstancesByResourceTags.html

.. _ListInstancesByResourceTags:

Querying an Instance by Tag
===========================

Function
--------

This API is used to query a specified instance by tag.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

A maximum of 20 tags can be added to a DB instance. The tag key must be unique.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/resource-instances/action

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                   | Description                                                                                                                                                                         |
   +=================+=================+========================================================================================+=====================================================================================================================================================================================+
   | offset          | No              | String                                                                                 | Index offset. The query starts from the next piece of data indexed by this parameter.                                                                                               |
   |                 |                 |                                                                                        |                                                                                                                                                                                     |
   |                 |                 |                                                                                        | -  If **action** is set to **count**, this parameter does not need to be transferred.                                                                                               |
   |                 |                 |                                                                                        | -  If **action** is set to **filter**, the parameter value must be a positive integer. The default value is **0**, indicating that the query starts from the first piece of data. ' |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String                                                                                 | Number of records to be queried.                                                                                                                                                    |
   |                 |                 |                                                                                        |                                                                                                                                                                                     |
   |                 |                 |                                                                                        | -  If **action** is set to **count**, this parameter does not need to be transferred.                                                                                               |
   |                 |                 |                                                                                        | -  If **action** is set to **filter**, the value ranges from **1** to **100**. If this parameter is not transferred, the first 100 instances are queried by default.                |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                                                                                 | Operation identifier.                                                                                                                                                               |
   |                 |                 |                                                                                        |                                                                                                                                                                                     |
   |                 |                 |                                                                                        | -  If **action** is set to **filter**, instances are queried based on tag filters.                                                                                                  |
   |                 |                 |                                                                                        | -  If **action** is set to **count**, only the total number of records is returned.                                                                                                 |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of :ref:`MatchOption <listinstancesbyresourcetags__request_matchoption>` objects | Search parameter.                                                                                                                                                                   |
   |                 |                 |                                                                                        |                                                                                                                                                                                     |
   |                 |                 |                                                                                        | -  If this parameter is not specified, the query is not based on the instance name or ID.                                                                                           |
   |                 |                 |                                                                                        | -  This parameter cannot be left blank.                                                                                                                                             |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of :ref:`TagOption <listinstancesbyresourcetags__request_tagoption>` objects     | Included tags. Each tag contains a maximum of 20 keys.                                                                                                                              |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listinstancesbyresourcetags__request_matchoption:

.. table:: **Table 4** MatchOption

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                    |
   +===========+===========+========+================================================================================================================================================+
   | key       | Yes       | String | Query criteria. The value can be **instance_name** or **instance_id**, indicating that the query is based on the instance name or instance ID. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | String | Name or ID of the instance to be queried                                                                                                       |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listinstancesbyresourcetags__request_tagoption:

.. table:: **Table 5** TagOption

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                               |
   +=================+=================+==================+===========================================================================================================================================================================================+
   | key             | Yes             | String           | Tag key. It can contain a maximum of 36 Unicode characters. The **key** value cannot be null, an empty string, or spaces. Before using **key**, delete spaces before and after the value. |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | .. note::                                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  |    The character set of this parameter is not verified during search.                                                                                                                     |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values          | Yes             | Array of strings | Tag values. Each tag value can contain a maximum of 43 Unicode characters and cannot contain spaces. Before using **values**, delete spaces before and after the value.                   |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | If the **values** is not specified, any parameter value can be queried. All values are in the OR relationship.                                                                            |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +-------------+-----------------------------------------------------------------------------------------------+--------------------------+
   | Parameter   | Type                                                                                          | Description              |
   +=============+===============================================================================================+==========================+
   | instances   | Array of :ref:`InstanceResult <listinstancesbyresourcetags__response_instanceresult>` objects | All instances.           |
   +-------------+-----------------------------------------------------------------------------------------------+--------------------------+
   | total_count | Integer                                                                                       | Total number of records. |
   +-------------+-----------------------------------------------------------------------------------------------+--------------------------+

.. _listinstancesbyresourcetags__response_instanceresult:

.. table:: **Table 7** InstanceResult

   +---------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Parameter     | Type                                                                                                | Description                                                                     |
   +===============+=====================================================================================================+=================================================================================+
   | instance_id   | String                                                                                              | Instance ID.                                                                    |
   +---------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | instance_name | String                                                                                              | Instance name.                                                                  |
   +---------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | tags          | Array of :ref:`InstanceTagResult <listinstancesbyresourcetags__response_instancetagresult>` objects | All tags. If there are no tags, **tags** is taken as an empty array by default. |
   +---------------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. _listinstancesbyresourcetags__response_instancetagresult:

.. table:: **Table 8** InstanceTagResult

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                         |
   +=======================+=======================+=====================================================================================================+
   | key                   | String                | Tag key. The tag key must be specified and can include a maximum of 36 Unicode characters.          |
   |                       |                       |                                                                                                     |
   |                       |                       | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | value                 | String                | Tag value. The tag value can contain a maximum of 43 Unicode characters and can be an empty string. |
   |                       |                       |                                                                                                     |
   |                       |                       | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/resource-instances/action

-  Example request body

   Querying an instance by name (Set **offset** to **100** and **limit** to **100**.)

   .. code-block::

      {
        "offset" : 100,
        "limit" : 100,
        "action" : "filter",
        "matches" : [{
          "key" : "instance_name",
          "value" : "test-single"
        }],
        "tags" : [{
          "key" : "key1",
          "values" : [ "value1", "value2" ]
        }]
      }

   Querying total records

   .. code-block::

      {
        "action" : "count",
        "tags" : [ {
          "key" : "key1",
          "values" : [ "value1", "value2" ]
        }, {
          "key" : "key2",
          "values" : [ "value1", "value2" ]
        } ],
        "matches" : [ {
          "key" : "instance_name",
          "value" : "test-single"
        }, {
          "key" : "instance_id",
          "value" : "958693039f284d6ebfb177375711072ein06"
        } ]
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total_count": 1,
     "instances" : [{
       "instance_id" : "2acbf2223caf3bac3c33c6153423c3ccin06",
       "instance_name" : "test-single",
       "tags" : [ {
         "key" : "key1",
         "value" : "value1"
       }, {
         "key" : "key2",
         "value" : "value1"
       } ]
     }]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
