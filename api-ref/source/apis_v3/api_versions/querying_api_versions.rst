:original_name: ListApiVersion.html

.. _ListApiVersion:

Querying API Versions
=====================

Function
--------

This API is used to query the supported API versions.

URI
---

GET https://{Endpoint}/

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 1** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                                     | Description             |
   +===========+==========================================================================================+=========================+
   | versions  | Array of :ref:`ApiVersionResponse <listapiversion__response_apiversionresponse>` objects | API version information |
   +-----------+------------------------------------------------------------------------------------------+-------------------------+

.. _listapiversion__response_apiversionresponse:

.. table:: **Table 2** ApiVersionResponse

   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                           | Description                                                                                           |
   +=======================+================================================================+=======================================================================================================+
   | id                    | String                                                         | API version number                                                                                    |
   +-----------------------+----------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | links                 | Array of :ref:`Links <listapiversion__response_links>` objects | API link information                                                                                  |
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

.. _listapiversion__response_links:

.. table:: **Table 3** Links

   +-----------+--------+-------------------------------------------------------------+
   | Parameter | Type   | Description                                                 |
   +===========+========+=============================================================+
   | href      | String | API URL. The value is **""**.                               |
   +-----------+--------+-------------------------------------------------------------+
   | rel       | String | The value is **self**, indicating that URL is a local link. |
   +-----------+--------+-------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/

Example Response
----------------

**Status code: 200**

Success

.. code-block::

   {
     "versions" : [ {
       "id" : "v3",
       "links" : [ ],
       "status" : "CURRENT",
       "version" : "",
       "min_version" : "",
       "updated" : "2019-10-30T17:34:02Z"
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
