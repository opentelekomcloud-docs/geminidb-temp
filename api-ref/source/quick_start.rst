:original_name: nosql_05_0011.html

.. _nosql_05_0011:

Quick Start
===========

This section describes how to create a GaussDB NoSQL instance by calling APIs.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently obtaining the token.

Involved APIs
-------------

If you use a token for authentication, you must obtain the user's token and add **X-Auth-Token** to the request message header of the service API when making an API call.

-  API for obtaining tokens from IAM
-  API for creating a GaussDB NoSQL instance

Procedure
---------

#. Use a token for authentication by referring to :ref:`Authentication <nosql_05_0009>`.

#. Send **POST https://{Endpoint}/v3/{project_id}/instances**.

#. Add **X-Auth-Token** to the request header.

#. Transfer the following parameters in the request body:

   .. note::

      Values of **region** and **availability_zone** are only for reference.

      For details about the API for creating instances, see :ref:`Creating an Instance <nosql_05_0014>`.

   .. code-block:: text

      {
          "name": "test-cassandra-01",//Instance name
          "datastore": {
               "type": "cassandra",//Database type
              "version": "3.11", //DB engine version
              "storage_engine": "rocksDB"//Storage engine
          },
          "region": "aaa",//Region
          "availability_zone": "bbb", //AZ
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",//VPC ID
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",//Subnet ID
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",//Security group ID
          "password": "xxxx",//Administrator password
          "mode": "Cluster", //Instance type
          "flavor": [
              {
                  "num": 3,//Nodes
                  "size": 500,//Storage space
                  "storage": "ULTRAHIGH", //Disk type
                  "spec_code": "geminidb.cassandra.4xlarge.4" //Resource specification code
              }
          ],
          "backup_strategy": {
              "start_time": "08:00-09:00",//Backup time window
              "keep_days": "8"//Retention period of backup files
          },
          "enterprise_project_id": "0"//Enterprise project ID
      }

   If the following information is displayed, the request is successful:

   .. code-block:: text

      {
          "id": "39b6a1a278844ac48119d86512e0000bin06",
          "name": "test-cassandra-01",
          "datastore": {
              "type": "cassandra",
              "version": "3.11",
              "storage_engine": "rocksDB"
          },
          "created": "2019-10-28 14:10:54",
          "status": "creating",
          "region": "aaa",
          "availability_zone": "bbb",
          "vpc_id": "674e9b42-cd8d-4d25-a2e6-5abcc565b961",
          "subnet_id": "f1df08c5-71d1-406a-aff0-de435a51007b",
          "security_group_id": "7aa51dbf-5b63-40db-9724-dad3c4828b58",
          "mode": "Cluster",
          "flavor": [
              {
                  "num": 3,
                  "size": 500,
                  "storage": "ULTRAHIGH",
                  "spec_code": "geminidb.cassandra.4xlarge.4"
              }
          ],
          "backup_strategy": {
              "start_time": "08:00-09:00",
              "keep_days": "8"
          },
          "job_id": "c010abd0-48cf-4fa8-8cbc-090f093eaa2f",
          "enterprise_project_id": "0"
      }

   If the request fails, an error code and error information are returned. For details, see :ref:`Error Codes <nosql_error_code>`.
