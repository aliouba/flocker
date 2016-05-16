.. Single Source Instructions

====================================
Installing the Flocker Node Services
====================================

.. begin-body-installing-node-intro

The following instructions describe how to install the ``clusterhq-flocker node`` package, and the optional ``clusterhq-flocker-docker-plugin`` package on each of the nodes in your cluster.

.. end-body-installing-node-intro

.. begin-body-installing-node-prereqs

Prerequisites
=============

Before you begin to install the Flocker node services, you will need the following:

* A minimum of 2 nodes:
  
  * We support installing the Flocker node services on either CentOS 7 or Ubuntu 14.04.
  * If you do not have any nodes, our guides listed below can be used to help you set up nodes, using Amazon Web Services, Rackspace, or Google Compute Engine.
  * To avoid potential disk space problems (for example, when storing popular Docker images), we recommend a minimum of 16 GB storage on each node.

* You will need permission for SSH access from your laptop.
* Depending on your usage of Flocker, you will require access to a range of ports.
  For example, instructions on specifying which ports to make available are included in the Amazon Web Services guide.
* Flocker's container management features depend on Docker.
  You will need to make sure `Docker (at least 1.8) is installed`_ and running.

.. end-body-installing-node-prereqs

.. begin-body-installing-node-guides

Helpful Guides for Setting Up Nodes
===================================

If you do not have any nodes, the following guides will help you set some up, with AWS, Rackspace, or GCE.

.. note:: If you set up nodes with AWS, Rackspace, or GCE, you'll need to come back to the installation steps below to install the ``flocker-node`` packages specific to your operating system.

.. end-body-installing-node-guides

.. XXX In the integration specific documentation, links to the guides appear here

.. begin-body-installing-node-rhel

Installing on RHEL 7
====================

.. note:: You should ensure your nodes are Flocker-ready, either by checking the prerequisites above, or by following our guides on using Amazon Web Services or Rackspace.

#. **Log into the first node as root:**

   .. prompt:: bash alice@mercury:~$

      ssh root@<your-first-node>

#. **Install the** ``clusterhq-flocker-node`` **package:**

   To install ``clusterhq-flocker-node`` on RHEL 7 you must install the RPM package provided by the ClusterHQ repository.
   The commands below will install the two repositories and the ``clusterhq-flocker-node`` package.
   
   Run the following commands as root on the target node:

   .. prompt:: bash [root@rhel]#

      yum list installed clusterhq-release || yum install -y https://clusterhq-archive.s3.amazonaws.com/centos/clusterhq-release$(rpm -E %dist).centos.noarch.rpm

      sed -i 's/$releasever/7/g' /etc/yum.repos.d/clusterhq.repo
      yum-config-manager --enable clusterhq
      yum install -y clusterhq-flocker-node

#. **Install the** ``clusterhq-flocker-docker-plugin`` **package:**

   At this point you can choose to install the Flocker plugin for Docker.
   Run the following command as root on the target node:

   .. prompt:: bash [root@rhel]#
   
      yum install -y clusterhq-flocker-docker-plugin

   .. XXX FLOC-3454 to create a task directive for installing the plugin

#. **Repeat the previous steps for all other nodes:**

   Log into your other nodes as root, and then complete step 2 and 3 until all the nodes in your cluster have installed the ``clusterhq-flocker-node`` and the optional ``clusterhq-flocker-docker-plugin`` package.

.. note:: Flocker's container management features depend on Docker.
          You will need to make sure `Docker (at least 1.8) is installed`_ and running.

.. end-body-installing-node-rhel

.. begin-body-installing-node-centos

Installing on CentOS 7
======================

.. note:: You should ensure your nodes are Flocker-ready, either by checking the prerequisites above, or by following our guides on using Amazon Web Services, Rackspace, or Google Compute Engine.

#. **Log into the first node as root:**

   .. prompt:: bash alice@mercury:~$

      ssh root@<your-first-node>

#. **Install the** ``clusterhq-flocker-node`` **package:**

   To install ``clusterhq-flocker-node`` on CentOS 7 you must install the RPM package provided by the ClusterHQ repository.
   The commands below will install the two repositories and the ``clusterhq-flocker-node`` package.
   
   Run the following commands as root on the target node:

   .. task:: install_flocker centos-7
      :prompt: [root@centos]#

#. **Install the** ``clusterhq-flocker-docker-plugin`` **package:**

   At this point you can choose to install the Flocker plugin for Docker.
   Run the following command as root on the target node:

   .. prompt:: bash [root@centos]#
   
      yum install -y clusterhq-flocker-docker-plugin

   .. XXX FLOC-3454 to create a task directive for installing the plugin

#. **Repeat the previous steps for all other nodes:**

   Log into your other nodes as root, and then complete step 2 and 3 until all the nodes in your cluster have installed the ``clusterhq-flocker-node`` and the optional ``clusterhq-flocker-docker-plugin`` package.

.. note:: Flocker's container management features depend on Docker.
          You will need to make sure `Docker (at least 1.8) is installed`_ and running.

.. end-body-installing-node-centos

.. begin-body-installing-node-ubuntu

Installing on Ubuntu 14.04
==========================

.. note:: You should ensure your nodes are Flocker-ready, either by checking the prerequisites above, or by following our guides on using Amazon Web Services, Rackspace, or Google Compute Engine.

#. **Log into the first node as root:**

   .. prompt:: bash alice@mercury:~$

      ssh root@<your-first-node>

#. **Install the** ``clusterhq-flocker-node`` **package:**

   To install ``clusterhq-flocker-node`` on Ubuntu 14.04 you must install the package provided by the ClusterHQ repository.
   The commands below will install the two repositories and the ``clusterhq-flocker-node`` package.
   
   Run the following commands as root on the target node:
   
   .. task:: install_flocker ubuntu-14.04
      :prompt: [root@ubuntu]#

#. **Install the** ``clusterhq-flocker-docker-plugin`` **package:**

   At this point you can choose to install the Flocker plugin for Docker.
   Run the following command as root on the target node:

   .. prompt:: bash [root@ubuntu]#
   
      apt-get install -y clusterhq-flocker-docker-plugin

   .. XXX FLOC-3454 to create a task directive for installing the plugin

#. **Repeat the previous steps for all other nodes:**

   Log into your other nodes as root, and then complete step 2 and 3 until all the nodes in your cluster have installed the ``clusterhq-flocker-node`` and the optional ``clusterhq-flocker-docker-plugin`` package.


.. note:: Flocker's container management features depend on Docker.
          You will need to make sure `Docker (at least 1.8) is installed`_ and running.

.. _Docker (at least 1.8) is installed: https://docs.docker.com/installation/

.. end-body-installing-node-ubuntu
