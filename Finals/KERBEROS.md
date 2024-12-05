![image](https://github.com/user-attachments/assets/bd408f09-19d5-49c2-88af-a251791e5f0a)


SYSADM1 -- Kerberos Lab Activity: A step-by-step Guide

> **Objective:**
>
> Set up a basic Kerberos authentication system to understand how
> Kerberos manages secure logins through
>
> ticket-based access.
>
> **Setup Requirements:**
>
> • Two VMs in Oracle VM, both running a Linux distribution like Ubuntu
> or CentOS.
>
> • VM1: Kerberos Server
>
> • VM2: Kerberos Client
>
> **Step 1: Initial Setup and Package Installation**
>
> 1\. **Update Packages on Both VMs:**
>
> o Open a terminal on each VM and run:
>
> *bash*
>
> *sudo apt update && sudo apt upgrade --y*

+-----------------------------------------------------------------------+
| ![](vertopal_396b0148d4                                               |
| b74b9e9fa2dfecd6b7e359/media/image2.png){width="3.4430544619422574in" |
| height="2.4375in"}                                                    |
|                                                                       |
| ![](vertopal_396b0148d4                                               |
| b74b9e9fa2dfecd6b7e359/media/image3.png){width="3.4680555555555554in" |
| height="2.4569433508311462in"}                                        |
+=======================================================================+
+-----------------------------------------------------------------------+

2\. **Install Kerberos Server Packages on VM1 (Kerberos Server):**\
o In VM1, install the Kerberos Key Distribution Center (KDC) and admin
server: *bash*\
*sudo apt install krb5-kdc krb5-admin-server --y*

+-----------------------------------------------------------------------+
| ![](vertopal_396b0148d                                                |
| 4b74b9e9fa2dfecd6b7e359/media/image4.png){width="4.748611111111111in" |
| height="0.8833333333333333in"}                                        |
|                                                                       |
| ![](vertopal_396b0148d                                                |
| 4b74b9e9fa2dfecd6b7e359/media/image5.png){width="4.727777777777778in" |
| height="0.7486100174978128in"}                                        |
+=======================================================================+
+-----------------------------------------------------------------------+

3\. **Install Kerberos Client Package on VM2 (Kerberos Client):** o In
VM2, install the Kerberos client software:

Page **2** of **6**

*bash*

*sudo apt install krb5-user -y*

+-----------------------------------+-----------------------------------+
| o                                 | > During installation, when       |
|                                   | > prompted, enter the Kerberos    |
|                                   | > realm you plan to set up, e.g., |
|                                   | > MYLAB.LOCAL.                    |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

**Step 2: Configure the Kerberos Server (VM1)**

1\. **Edit the Kerberos Configuration File:**

> o Open /etc/krb5.conf for editing:

*bash*

*sudo nano /etc/krb5.conf*

+-----------------------------------+-----------------------------------+
| o                                 | > Set the realm as MYLAB.LOCAL.   |
|                                   | > You should also specify the KDC |
|                                   | > and admin server as VM1's       |
|                                   | > hostname or IP address:         |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

ini

\[libdefaults\]

> default_realm = MYLAB.LOCAL

+-----------------------------------------------------------------------+
| ![](vertopal_396b0148d                                                |
| 4b74b9e9fa2dfecd6b7e359/media/image6.png){width="4.484721128608924in" |
| height="1.0902777777777777in"}                                        |
|                                                                       |
| ![](vertopal_396b0148d                                                |
| 4b74b9e9fa2dfecd6b7e359/media/image7.png){width="4.413888888888889in" |
| height="0.44166666666666665in"}                                       |
+=======================================================================+
+-----------------------------------------------------------------------+

Page **3** of **6**

\[realms\]\
MYLAB.LOCAL = {\
kdc = \<VM1_IP_or_hostname\>\
admin_server = \<VM1_IP_or_hostname\>\
}

o Save and close the file (Ctrl+X, then Y, and Enter to confirm). 2.
**Initialize the Kerberos Database:**

o Create the database for the Kerberos realm: *bash*\
*sudo krb5_newrealm*

o You will be prompted to set a password for the Kerberos database. 3.
**Start and Enable the Kerberos Services:**

o Start the KDC and admin server, and ensure they start automatically on
boot: *bash*\
*sudo systemctl start krb5-kdc*\
*sudo systemctl start krb5-admin-server*\
*sudo systemctl enable krb5-kdc*\
*sudo systemctl enable krb5-admin-server*

  ---------------------------------------------------------------------------------------------
  ![](vertopal_396b0148d4b74b9e9fa2dfecd6b7e359/media/image8.png){width="4.798611111111111in"
  height="1.9166655730533684in"}
  ---------------------------------------------------------------------------------------------

  ---------------------------------------------------------------------------------------------

**Step 3: Set Up a Kerberos User Principal**\
1. **Create a New User Principal:**

> o Run the following command to create a test user in the Kerberos
> realm:

Page **4** of **6**

*bash*

*sudo kadmin.local -q \"addprinc testuser@MYLAB.LOCAL\"*

+-----------------------------------+-----------------------------------+
| o                                 | > Set a password for testuser.    |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

  ---------------------------------------------------------------------------------------------
  ![](vertopal_396b0148d4b74b9e9fa2dfecd6b7e359/media/image9.png){width="4.901388888888889in"
  height="1.095832239720035in"}
  ---------------------------------------------------------------------------------------------

  ---------------------------------------------------------------------------------------------

2\. **Verify the User Principal:**

> o To confirm the principal is created, list all principals:

*bash*

*sudo kadmin.local -q \"listprincs\"*

  ----------------------------------------------------------------------------------------------
  ![](vertopal_396b0148d4b74b9e9fa2dfecd6b7e359/media/image10.png){width="4.861111111111111in"
  height="1.1027766841644795in"}
  ----------------------------------------------------------------------------------------------

  ----------------------------------------------------------------------------------------------

**Step 4: Configure the Kerberos Client (VM2)**\
1. **Edit the Kerberos Configuration File on VM2:**

> o Open /etc/krb5.conf for editing on VM2:

*bash*

*sudo nano /etc/krb5.conf*

+-----------------------------------+-----------------------------------+
|   ------------------------------  |                                   |
|                                   |                                   |
|   ------------------------------  |                                   |
|                                   |                                   |
| > ![](vertopal_396b0148d4b7       |                                   |
| 4b9e9fa2dfecd6b7e359/media/image7 |                                   |
| .png){width="7.026388888888889in" |                                   |
| > height="0.7041666666666667in"}  |                                   |
+===================================+===================================+
| o                                 | > Set the default realm to        |
|                                   | > MYLAB.LOCAL and point to the    |
|                                   | > KDC and admin server on VM1.    |
|                                   | > The configuration should match  |
|                                   | > what you set on VM1.            |
+-----------------------------------+-----------------------------------+

Page **5** of **6**

  -----------------------------------------------------------------------------------
  ![](vertopal_396b0148d4b74b9e9fa2dfecd6b7e359/media/image11.png){width="6.1125in"
  height="1.3027777777777778in"}
  -----------------------------------------------------------------------------------

  -----------------------------------------------------------------------------------

**Step 5: Test Kerberos Authentication**

1\. **Request a Kerberos Ticket for the User on VM2:**

> o In the terminal on VM2, request a ticket for testuser:

*bash*

*kinit*

+-----------------------------------+-----------------------------------+
|   ------------------------------  |                                   |
|                                   |                                   |
|   ------------------------------  |                                   |
|                                   |                                   |
| > ![](vertopal_396b0148d4b74      |                                   |
| b9e9fa2dfecd6b7e359/media/image12 |                                   |
| .png){width="7.026388888888889in" |                                   |
| > height="0.5527777777777778in"}  |                                   |
+===================================+===================================+
| o                                 | > Enter the password you set for  |
|                                   | > testuser.                       |
+-----------------------------------+-----------------------------------+

2\. **Verify the Ticket:**

> o Check if the ticket was issued by listing active Kerberos tickets:

*bash*

*klist*

+-----------------------------------+-----------------------------------+
|   ------------------------------  |                                   |
|                                   |                                   |
|   ------------------------------  |                                   |
|                                   |                                   |
| > ![](vertopal_396b0148d4b74      |                                   |
| b9e9fa2dfecd6b7e359/media/image13 |                                   |
| .png){width="7.026388888888889in" |                                   |
| > height="0.6194433508311461in"}  |                                   |
+===================================+===================================+
| o                                 | > You should see details about    |
|                                   | > the ticket, such as the         |
|                                   | > principal and expiration time,  |
|                                   | > confirming successful Kerberos  |
|                                   | > authentication.                 |
+-----------------------------------+-----------------------------------+

Page **6** of **6**
