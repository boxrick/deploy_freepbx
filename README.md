deploy_freepbx
=========
[![Build Status](https://travis-ci.org/boxrick/deploy_freepbx.svg?branch=master)](https://travis-ci.org/boxrick/deploy_freepbx)

This role installs Freepbx, Asterisk and all the required mass of packages needed on a CentOS 7.x


Requirements
------------

This module requires Ansible 2.2


Role Variables
--------------

See defaults for variables and descriptions


Description
----------------

The intention of this role is to take everything here and place it into a role, it will basically take a fresh CentOS 7.XX system and deploy asterisk 14 and the latest Freepbx on the same machine.

To test this locally simple move into the 'tests' folder. Have Vagrant, Virtualbox and Ansible installed. Then type

`vagrant up`

Once it has done installing and configuring open a web browser and navigate to http://127.0.0.1:8080 or https://127.0.0.1:4443  

https://wiki.freepbx.org/display/FOP/Installing+FreePBX+14+on+CentOS+7

Things to be aware of

* No iptables or firewalld configured, this will be an open system. After deploy it will be ready to be configured by the GUI and an IP
* As of 10/09/17 this works fine on a digital ocean Droplet.
* There are a few callouts to scripts in some of the source code, this can be worked around but will need to dissect these scripts and hope the source code doesn't change too much.
* Because much of this is pulling down tarballs and doing configure and make installs, there have been a number of static assumptions made based on the file it creates. This is to prevent 'changed' each time and make the code imutable.

So this is a starting point, my hope is to simplify the install of FreePBX and for people who wish to use it without all the commercial modules but still get the usage of the excellent GUI provided by FreePBX.

Example Playbook
----------------

Example to call:

    - hosts: all
      roles:
         - { role: deploy_freepbx }
