:original_name: nosql_10_0100.html

.. _nosql_10_0100:

Querying Tasks and Details
==========================

Function
--------

This API is used to query tasks (by default) and details.

URI
---

GET https://{Endpoint}/v3/{project_id}/jobs

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================+
   | id              | No              | String          | Task ID.                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | No              | String          | Query start time in the "yyyy-mm-ddThh:mm:ssZ" format. The default value is 30 days before the current date.                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset.                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | No              | String          | End time (the current time by default) in the "yyyy-mm-ddThh:mm:ssZ" format. It must be later than the start time and the time span cannot exceed 30 days.                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset.                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Task status. The value can be: **Running**, indicating that the task is being executed. **Completed**, indicating that the task is completed. **Failed**, indicating that the task fails.                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Task name.                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | -  **CreateInstance**: Create an instance.                                                                                                                                                                                  |
   |                 |                 |                 | -  **RestoreNewInstance**: Restore data to a new instance.                                                                                                                                                                  |
   |                 |                 |                 | -  **EnlargeInstance**: Add nodes.                                                                                                                                                                                          |
   |                 |                 |                 | -  **ReduceInstance**: Delete nodes.                                                                                                                                                                                        |
   |                 |                 |                 | -  **RestartInstance**: Restart an instance.                                                                                                                                                                                |
   |                 |                 |                 | -  **RestartNode**: Restart a node.                                                                                                                                                                                         |
   |                 |                 |                 | -  **EnlargeInstanceVolume**: Scale up storage space of an instance.                                                                                                                                                        |
   |                 |                 |                 | -  **ReduceInstanceVolume**: Scale in storage space of an instance.                                                                                                                                                         |
   |                 |                 |                 | -  **ResizeInstance**: Change the specifications of an instance.                                                                                                                                                            |
   |                 |                 |                 | -  **UpgradeDbVersion**: Upgrade the engine version.                                                                                                                                                                        |
   |                 |                 |                 | -  **BindPublicIP**: Bind an EIP to an instance.                                                                                                                                                                            |
   |                 |                 |                 | -  **UnbindPublicIP**: Unbind an EIP from an instance.                                                                                                                                                                      |
   |                 |                 |                 | -  **DeleteInstance**: Delete an instance.                                                                                                                                                                                  |
   |                 |                 |                 | -  **EnlargeInstanceColdVolume**: Scale up cold storage of an instance.                                                                                                                                                     |
   |                 |                 |                 | -  **AddInstanceColdVolume**: Enable cold storage for an instance.                                                                                                                                                          |
   |                 |                 |                 | -  **ModifySecurityGroup**: Modify a security group.                                                                                                                                                                        |
   |                 |                 |                 | -  **ModifyCcmCert**: Modify a CCM certificate.                                                                                                                                                                             |
   |                 |                 |                 | -  **ModifyPort**: Change a port.                                                                                                                                                                                           |
   |                 |                 |                 | -  **ConstructDisasterRecovery**: Establish a DR relationship.                                                                                                                                                              |
   |                 |                 |                 | -  **DeConstructDisasterRecovery**: Remove a DR relationship.                                                                                                                                                               |
   |                 |                 |                 | -  **SwitchOverDisasterRecovery**: Switch a DR relationship.                                                                                                                                                                |
   |                 |                 |                 | -  **BuildBiActiveInstance**: Create an instance with a dual-active DR relationship.                                                                                                                                        |
   |                 |                 |                 | -  **ReleaseBiActiveInstance**: Remove a dual-active relationship from an instance.                                                                                                                                         |
   |                 |                 |                 | -  **BackupInstance**: Back up an instance.                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | If **offset** is set to *N*, the resource query starts from the *N*\ +1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of records to be queried. The value can be **10**, **20**, or **50**. The default value is **50**.                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------+---------------------------------------------------------------------------+-----------------------------------------+
   | Parameter   | Type                                                                      | Description                             |
   +=============+===========================================================================+=========================================+
   | jobs        | Array of objects (:ref:`Table 5 <nosql_10_0100__response_slowlogresult>`) | Task list.                              |
   +-------------+---------------------------------------------------------------------------+-----------------------------------------+
   | total_count | Integer                                                                   | Total number of tasks in the task list. |
   +-------------+---------------------------------------------------------------------------+-----------------------------------------+

.. _nosql_10_0100__response_slowlogresult:

.. table:: **Table 5** JobDetail

   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                         | Description                                                                                                                                                                                                                        |
   +=======================+==============================================================+====================================================================================================================================================================================================================================+
   | id                    | String                                                       | Task ID.                                                                                                                                                                                                                           |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                       | Task name.                                                                                                                                                                                                                         |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                       | Task execution status. The value can be: **Running**, indicating that the task is being executed. **Completed** indicating that the task has been successfully executed. **Failed** indicating that the task fails to be executed. |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time            | String                                                       | Creation time in the "yyyy-mm-ddThh:mm:ssZ" format.                                                                                                                                                                                |
   |                       |                                                              |                                                                                                                                                                                                                                    |
   |                       |                                                              | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. For example, in the Beijing time zone, the offset is **+0800**.                                                         |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                                                       | End time in the yyyy-mm-ddThh:mm:ssZ format.                                                                                                                                                                                       |
   |                       |                                                              |                                                                                                                                                                                                                                    |
   |                       |                                                              | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. For example, in the Beijing time zone, the offset is **+0800**.                                                         |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | progress              | String                                                       | Task execution progress.                                                                                                                                                                                                           |
   |                       |                                                              |                                                                                                                                                                                                                                    |
   |                       |                                                              | .. note::                                                                                                                                                                                                                          |
   |                       |                                                              |                                                                                                                                                                                                                                    |
   |                       |                                                              |    The execution progress (such as **"60%"**, indicating the task execution progress is 60%) is displayed only when the task is being executed. Otherwise, **""** is returned.                                                     |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance              | Objects in :ref:`Table 6 <nosql_10_0100__table762814573276>` | Details of the instance associated with the task.                                                                                                                                                                                  |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                                                       | Task failure information.                                                                                                                                                                                                          |
   +-----------------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_10_0100__table762814573276:

.. table:: **Table 6** JobInstanceInfo

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   id        String Instance ID.
   name      String Instance name.
   ========= ====== ==============

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/jobs?id=89a0cde6-9c46-4b89-a92c-573e1083ff23

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total_count" : 1,
     "jobs" : [ {
       "id" : "6f85e061-04dd-42e7-86d6-d3b1e40aac2e",
       "name" : "CreateCassandra",
       "status" : "Running",
       "start_time" : "2023-09-12T06:44:01+0000",
       "end_time" : "2023-09-12T06:44:03+0000",
       "progress" : "14%",
       "instance" : {
         "id" : "27a045b6bf9e46f691f81366d398cb04in06",
         "name" : "nosql-12f5"
       },
       "fail_reason" : ""
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
