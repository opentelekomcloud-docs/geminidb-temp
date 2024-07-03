:original_name: nosql_03_0016.html

.. _nosql_03_0016:

Resetting the Administrator Password
====================================

Scenarios
---------

For security reasons, change administrator passwords periodically.

Precautions
-----------

If the instance status is **Available**, **Backing up**, **Checking restoration**, **Scaling up** or certain nodes become abnormal, you can reset the administrator password.

Method 1
--------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instance Management** page, locate the DB instance you wish to reset the password for and choose **More** > **Reset Password** in the **Operation** column.

#. Enter and confirm the new administrator password and click **OK**.

   The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``

Method 2
--------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instance Management** page, click the DB instance you wish to reset the password for. The **Basic Information** page is displayed.

#. In the **DB Information** area, click **Reset Password** in the **Administrator** field.

#. Enter and confirm the new administrator password and click **OK**.

   The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``
