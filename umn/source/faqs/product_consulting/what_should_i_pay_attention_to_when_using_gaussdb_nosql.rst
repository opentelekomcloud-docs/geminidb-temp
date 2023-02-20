:original_name: nosql_faq_0002.html

.. _nosql_faq_0002:

What Should I Pay Attention to When Using GaussDB NoSQL?
========================================================

#. DB instances' operating systems (OSs) are invisible to you. Your applications can only access a database through an IP address and port.

#. The backup files stored in OBS and the system containers used by GaussDB NoSQL are invisible to you. They are visible only in the GaussDB NoSQL management system.

#. Precautions after purchasing DB instances:

   After purchasing DB instances, you do not need to perform basic database O&M operations, such as applying HA and security patches, but you should still note:

   a. The CPU, input/output operations per second (IOPS), and space are insufficient for the DB instances.
   b. The DB instance has performance problems and whether optimization is required.
