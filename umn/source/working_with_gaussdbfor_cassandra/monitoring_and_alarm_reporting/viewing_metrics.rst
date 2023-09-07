:original_name: nosql_03_0013.html

.. _nosql_03_0013:

Viewing Metrics
===============

Scenarios
---------

Cloud Eye monitors GaussDB NoSQL running statuses. You can obtain the monitoring metrics of GaussDB NoSQL on the management console.

Monitored data requires a period of time for transmission and display. The status of the monitored object displayed on the Cloud Eye page is the status obtained 5 to 10 minutes before. You can view the monitored data of a newly created DB instance 5 to 10 minutes later.

Prerequisites
-------------

-  The DB instance is running properly.

   Cloud Eye does not display the metrics of a faulty or deleted DB instance. You can view the monitoring information only after the instance is restarted or recovered.

-  The DB instance has been properly running for at least 10 minutes.

   The monitoring data and graphics are available for a new DB instance after the instance runs for at least 10 minutes.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the target DB instance.

#. In the **Node Information** area on the **Basic Information** page, click **View Metric** in the **Operation** column.

#. In the monitoring area, you can select a duration to view the monitoring data.

   You can view the monitoring data of the service in the last 1, 3, or 12 hours.

   To view the monitoring curve in a longer time range, click |image1| to enlarge the graph.

.. |image1| image:: /_static/images/en-us_image_0000001092506886.png
