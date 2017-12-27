Couchbase PoC
=======
This repository contains will allow you to deploy a basic Couchbase server based on **CentOS 6.6** and  **Couchbase Community Edition 5.0.1 build 5003** using **Vagrant** and **Ansible**

You can find all variables needed to access to your new brand cluster on vars directory

In order to develop this, some assumptions have been made:

 - VirtualBox is used as provider
 - Ansible is used as provisioner for VM's
 - Network for VM's are provided using a bridge adapter, so if you have more than 1 interface in your physical host you'll need to specify on which interface you want to create the bridge
 - A DHCP server is running on your network, in order to provide automatic network configuration for your VM's
