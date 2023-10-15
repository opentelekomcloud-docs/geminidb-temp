:original_name: nosql_abnormal_result.html

.. _nosql_abnormal_result:

Abnormal Request Results
========================

-  Abnormal Response

   .. table:: **Table 1** Parameter description

      +------------+-----------+--------+---------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                         |
      +============+===========+========+=====================================================================+
      | error_code | Yes       | String | Error code returned when a task submission exception occurs.        |
      +------------+-----------+--------+---------------------------------------------------------------------+
      | error_msg  | Yes       | String | Error description returned when a task submission exception occurs. |
      +------------+-----------+--------+---------------------------------------------------------------------+

-  Example abnormal response

   .. code-block:: text

      {
          "error_code": "DBS.200001",
          "error_msg": "Parameter error"
      }
