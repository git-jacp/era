.. title:: Nutanix Era Labs

.. toctree::
  :maxdepth: 2
  :caption: Era Tech Summit 2019 Lab
  :name: _era_tech_summit_2019_lab
  :hidden:

  era/era

.. toctree::
  :maxdepth: 2
  :caption: Era Labs
  :name: _era_labs
  :hidden:

  era_deploy_and_register/era_deploy_and_register
  era_provision_postgresdb/era_provision_postgresdb
  era_clone_postgresdb/era_clone_postgresdb

.. toctree::
  :maxdepth: 2
  :caption: Optional Labs
  :name: _optional_labs
  :hidden:

  sshkey_creation/sshkey_creation

.. _getting_started:

---------------
Getting Started
---------------

Welcome to the Nutanix Era Labs! This workbook accompanies an instructor-led session that introduces Nutanix Era and many common management tasks. Each section has a lesson and an exercise to give you hands-on practice. The instructor explains the exercises and answers any additional questions that you may have.

What's New
++++++++++

- Workshop updated for the following software versions:
    - AOS & PC 5.10.x

- Optional Lab Updates:

Agenda
++++++

- Nutanix Era Labs
    - Era: Deploy and Register
    - Era: Provision Postgres DB
    - Era: Clone Postgres DB
    - Calm: Windows Blueprint
    - Calm: Marketplace

- Optional Labs
    - SSHKey Creation

Introductions
+++++++++++++

- Name
- Familiarity with Nutanix

Initial Setup
+++++++++++++

- Take note of the *Passwords* being used.
- Log into your virtual desktops (connection info below)

Environment Details
+++++++++++++++++++

Nutanix Workshops are intended to be run in the Nutanix Hosted POC environment. Your cluster will be provisioned with all necessary images, networks, and VMs required to complete the exercises.

Networking
..........

Hosted POC clusters follow a standard naming convention:

- **Cluster Name** - POC\ *XYZ*
- **Subnet** - 10.**21**.\ *XYZ*\ .0
- **Cluster IP** - 10.**21**.\ *XYZ*\ .37

If provisioned from the marketing pool:

- **Cluster Name** - MKT\ *XYZ*
- **Subnet** - 10.**20**.\ *XYZ*\ .0
- **Cluster IP** - 10.**20**.\ *XYZ*\ .37

For example:

- **Cluster Name** - POC055
- **Subnet** - 10.21.55.0
- **Cluster IP** - 10.21.55.37

Throughout the Workshop there are multiple instances where you will need to substitute *XYZ* with the correct octet for your subnet, for example:

.. list-table::
  :widths: 25 75
  :header-rows: 1

  * - IP Address
    - Description
  * - 10.21.\ *XYZ*\ .37
    - Nutanix Cluster Virtual IP
  * - 10.21.\ *XYZ*\ .39
    - **PC** VM IP, Prism Central
  * - 10.21.\ *XYZ*\ .40
    - **DC** VM IP, NTNXLAB.local Domain Controller

Each cluster is configured with 2 VLANs which can be used for VMs:

.. list-table::
  :widths: 25 25 10 40
  :header-rows: 1

  * - Network Name
    - Address
    - VLAN
    - DHCP Scope
  * - Primary
    - 10.21.\ *XYZ*\ .1/25
    - 0
    - 10.21.\ *XYZ*\ .50-10.21.\ *XYZ*\ .124
  * - Secondary
    - 10.21.\ *XYZ*\ .129/25
    - *XYZ1*
    - 10.21.\ *XYZ*\ .132-10.21.\ *XYZ*\ .253

Credentials
...........

.. note::

  The *<Cluster Password>* is unique to each cluster and will be provided by the leader of the Workshop.

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Credential
    - Username
    - Password
  * - Prism Element
    - admin
    - *<Cluster Password>*
  * - Prism Central
    - admin
    - *<Cluster Password>*
  * - Controller VM
    - nutanix
    - *<Cluster Password>*
  * - Prism Central VM
    - nutanix
    - *<Cluster Password>*

Each cluster has a dedicated domain controller VM, **DC**, responsible for providing AD services for the **NTNXLAB.local** domain. The domain is populated with the following Users and Groups:

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Group
    - Username(s)
    - Password
  * - Administrators
    - Administrator
    - nutanix/4u
  * - SSP Admins
    - adminuser01-adminuser25
    - nutanix/4u
  * - SSP Developers
    - devuser01-devuser25
    - nutanix/4u
  * - SSP Power Users
    - poweruser01-poweruser25
    - nutanix/4u
  * - SSP Basic Users
    - basicuser01-basicuser25
    - nutanix/4u

Access Instructions
+++++++++++++++++++

The Nutanix Hosted POC environment can be accessed a number of different ways:

Citrix XenDesktop
.................

https://citrixready.nutanix.com - *Accessible via the Citrix Receiver client or HTML5*

**Nutanix Employees** - Use your NUTANIXDC credentials

**Non-Employees** - **Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Employee Pulse Secure VPN
..........................

https://sslvpn.nutanix.com - Use your CORP credentials

Non-Employee Pulse Secure VPN
..............................

https://lab-vpn.nutanix.com - **Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Under **Client Application Sessions**, click **Start** to the right of **Pulse Secure** to download the client.

Install and open **Pulse Secure**.

Add a connection:

- **Type** - Policy Secure (UAC) or Connection Server
- **Name** - HPOC VPN
- **Server URL** - lab-vpn.nutanix.com
