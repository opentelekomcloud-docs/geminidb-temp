:original_name: nosql_02_0008.html

.. _nosql_02_0008:

Binding an EIP
==============

Scenarios
---------

The Elastic IP service provides independent public IP addresses and bandwidth for Internet access. After you create a GaussDB(for Cassandra) instance, you can bind an EIP to it to allow external access. If later you want to prohibit external access, you can also unbind the EIP from the DB instance.

Precautions
-----------

-  Before accessing a database, you need to apply for an EIP on the VPC console. Then, add an inbound rule to allow the IP addresses or IP address ranges of ECSs. For details, see section :ref:`Configuring Security Group Rules <nosql_02_0011>`.
-  To change the EIP that has been bound to a node, you need to unbind it from the node first.

.. _nosql_02_0008__en-us_topic_0221158678_section1664218463351:


Binding an EIP
--------------

#. On the **Instance Management** page, click the target GaussDB(for Cassandra) instance.

#. On the **Basic Information** page, in the **Node Information** area, locate the target node and click **Bind EIP** in the **Operation** column.

#. In the displayed dialog box, all available unbound EIPs are listed. Select the required EIP and click **OK**. If no available EIPs are displayed, click **View EIP** and create an EIP on the VPC console.

#. In the **EIP** column, view the EIP that is successfully bound.

   To unbind the EIP from the DB instance, see :ref:`Unbinding an EIP <nosql_02_0008__en-us_topic_0221158678_section1364313461356>`.

.. _nosql_02_0008__en-us_topic_0221158678_section1364313461356:

Unbinding an EIP
----------------

#. On the **Instance Management** page, click the target GaussDB(for Cassandra) instance.

#. On the **Basic Information** page, in the **Node Information** area, locate the target node and click **Unbind EIP** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   To bind an EIP to the DB instance again, see :ref:`Binding an EIP <nosql_02_0008__en-us_topic_0221158678_section1664218463351>`.
