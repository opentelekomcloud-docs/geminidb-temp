:original_name: nosql_faq_0003.html

.. _nosql_faq_0003:

What Is Instance Availability?
==============================

Formula for a GaussDB NoSQL instance availability:

DB instance availability = (1 - Failure duration/Total service duration) x 100%.

The failure duration refers to the total duration of faults that occur during the running of a DB instance after you create the instance. The total service duration refers to the total running time of the DB instance.
