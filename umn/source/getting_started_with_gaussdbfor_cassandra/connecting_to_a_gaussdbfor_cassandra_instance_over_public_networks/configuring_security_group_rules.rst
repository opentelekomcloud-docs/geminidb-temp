:original_name: nosql_02_0011.html

.. _nosql_02_0011:

Configuring Security Group Rules
================================

**Scenarios**
-------------

The default security group rule allows all outgoing data packets. ECSs and GaussDB(for Cassandra) instances in the same security group can access each other. After a security group is created, you can create different rules for that security group, which allows you to control access to the GaussDB(for Cassandra) instances that in it.

This section describes how to create a security group to enable specific IP addresses and ports to access GaussDB(for Cassandra) instances.

**Precautions**
---------------

-  By default, you can create up to 500 security group rules. However, too many rules increase network latency for initial access, so it is recommended that you add no more than 50 rules for each security group.
-  To access a GaussDB(for Cassandra) instance from resources outside the security group, you need to configure an inbound rule to allow access to the GaussDB(for Cassandra) instance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click the security group name.
#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed **Add Inbound Rule** dialog box, set required parameters to add inbound rules. On the **Outbound Rules** tab, click **Add Rule**. In the displayed **Add Outbound Rule** dialog box, set required parameters to add outbound rules.
#. In the displayed dialog box, set required parameters.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001139129187.png
