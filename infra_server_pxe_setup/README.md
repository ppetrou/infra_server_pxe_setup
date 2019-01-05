infra_server_pxe_setup
=========

Simple role to setup a PXE Boot Server supporting the following configurations:

- Install CentOS 7 x64 with Local Repo
- Install CentOS 7 x64 with http://mirror.centos.org Repo
- Install CentOS 7 x64 with Local Repo using VNC
- Boot from local drive

Requirements
------------

NA

Role Variables
--------------

```
interface: enp0s3
domain: local 
pxe_server_ip: 192.168.1.230

dhcp_start: 192.168.1.200
dhcp_end: 192.168.1.220
dhcp_mask: 255.255.255.0
dhcp_lease: 1h

gateway_ip: 0.0.0.0
dns_server_ip: 192.168.1.254
dns_forwarder_ip: 8.8.4.4
broadcast_ip: 192.168.1.255
ntp_server_ip: 0.0.0.0
```

Dependencies
------------

NA

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
---
- hosts: pxe_server
  become: yes
  roles:
    - { role: infra_server_pxe_setup } 
```         
         
License
-------

BSD

Author Information
------------------

Petros Petrou - ppetrou@gmail.com

