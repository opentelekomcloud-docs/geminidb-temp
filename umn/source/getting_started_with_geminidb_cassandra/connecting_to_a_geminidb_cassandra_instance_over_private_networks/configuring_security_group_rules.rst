:original_name: nosql_02_0004.html

.. _nosql_02_0004:

Configuring Security Group Rules
================================

**Scenarios**
-------------

The default security group rule allows all outgoing data packets. ECSs and GeminiDB instances in the same security group can access each other. After a security group is created, you can create different rules for that security group, which allows you to control access to the GeminiDB instances that in it.

The following describes how to set security groups.

**Precautions**
---------------

-  If the ECS and DB instance are in the same security group, they can communicate with each other by default. No security group rule needs to be configured.
-  If the ECS and DB instance are in different security groups, you need to configure security group rules for the ECS and DB instance separately.

   -  To allow access to the GeminiDB Cassandra instance, you need to configure an inbound rule for the security group that the instance nodes belong to.
   -  By default, the security group allows all outbound data packets, so you do not need to configure a security rule for the ECS. If not all access from the ECS is allowed, you need to configure an outbound rule for the ECS.

-  By default, you can create up to 500 security group rules. However, too many rules increase network latency for initial access, so it is recommended that you add no more than 50 rules for each security group.

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

.. |image1| image:: /_static/images/en-us_image_0000001815205124.png
