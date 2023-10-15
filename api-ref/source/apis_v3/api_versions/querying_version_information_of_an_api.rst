:original_name: ShowApiVersion.html

.. _ShowApiVersion:

Querying Version Information of an API
======================================

Function
--------

This API is used to query version information of a specified API.

URI
---

GET https://{Endpoint}/{versionId}

.. table:: **Table 1** Path parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   versionId Yes       String API version
   ========= ========= ====== ===========

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+--------------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                           | Description             |
   +===========+================================================================================+=========================+
   | version   | :ref:`ApiVersionResponse <showapiversion__response_apiversionresponse>` object | API version information |
   +-----------+--------------------------------------------------------------------------------+-------------------------+

.. _showapiversion__response_apiversionresponse:

.. table:: **Table 3** ApiVersionResponse

   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                           | Description                                                                                           |
   +=======================+================================================================+=======================================================================================================+
   | id                    | String                                                         | API version number                                                                                    |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | links                 | Array of :ref:`Links <showapiversion__response_links>` objects | API link information                                                                                  |
   |                       |                                                                |                                                                                                       |
   |                       |                                                                | .. note::                                                                                             |
   |                       |                                                                |                                                                                                       |
   |                       |                                                                |    If the version is v3, the value is **[]**.                                                         |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | status                | String                                                         | Version status                                                                                        |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | version               | String                                                         | Subversion information of the API version                                                             |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | min_version           | String                                                         | Minimum API version number                                                                            |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | updated               | String                                                         | Version update time                                                                                   |
   |                       |                                                                |                                                                                                       |
   |                       |                                                                | The format is yyyy-mm-dd Thh:mm:ssZ.                                                                  |
   |                       |                                                                |                                                                                                       |
   |                       |                                                                | **T** is the separator between the calendar and the hourly notation of time. **Z** indicates the UTC. |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _showapiversion__response_links:

.. table:: **Table 4** Links

   +-----------+--------+-------------------------------------------------------------+
   | Parameter | Type   | Description                                                 |
   +===========+========+=============================================================+
   | href      | String | API URL. The value is **""**.                               |
   +-----------+--------+-------------------------------------------------------------+
   | rel       | String | The value is **self**, indicating that URL is a local link. |
   +-----------+--------+-------------------------------------------------------------+

Request Example
---------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3

Example Response
----------------

**Status code: 200**

Success

.. code-block::

   {
     "version" : {
       "id" : "v3",
       "links" : [ ],
       "status" : "CURRENT",
       "version" : "",
       "min_version" : "",
       "updated" : "2019-10-30T17:34:02Z"
     }
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
