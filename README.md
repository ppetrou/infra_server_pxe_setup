infra_server_pxe_setup
=========

Simple role to setup a PXE Boot Server supporting the following configurations:

- Install CentOS 7 x64 with Local Repo
- Install CentOS 7 x64 with http://mirror.centos.org Repo
- Install CentOS 7 x64 with Local Repo using VNC
- Boot from local drive

Is it based on the following blog:

https://www.tecmint.com/install-pxe-network-boot-server-in-centos-7/

Requirements
------------

NA

Role Variables
--------------

```

Variable                                Level       Description                                                         

interface                               Default     PXE Server NIC                                                      
domain                                  Default     PXE Server Domain                                                   
pxe_server_ip                           Default     PXE Server IP Address. It must match the interface NIC address!     
dhcp_start                              Default     DHCP Start Address                                                  
dhcp_end                                Default     DHCP End Address                                                    
dhcp_mask                               Default     DHCP Mask                                                           
dhcp_lease                              Default     DHCP Lease Time                                                     
gateway_ip                              Default     DHCP Gateway                                                        
dns_server_ip                           Default     DHCP DNS Server IP                                                  
dns_forwarder_ip                        Default     DHCP DNS Forwarder IP                                               
broadcast_ip                            Default     DHCP Broadcast IP                                                   
ntp_server_ip                           Default     DHCP NTP Server IP                                                  
centos_download_url                     Default     Centos 7 Download URL                                              
centos_iso_filename                     Default     Centos 7 ISO Filename                                               
centos_test_installation_source_url     Default     Centos 7 URL to test if installation media is available on server. 

dhcp_options                            Vars        List with DHCP Options. Should not be changed. See Note 1           
pxe_prompt                              Vars        The message that PXE Server prompts on Boot. 
pxe_prompt_timeout                      Vars        The PXE Server message timeout
architecture                            Vars        PXE Service Architecture
pxe_service_message                     Vars        PXE Service Message
tftp_root                               Vars        Default TFTP Installation Directory.

NOTE 1. Var dhcp options is looped in dnsmasq.conf.j2 template and populates the configuration for the DHCP Server. If changed you need to verify the DHCP Option Tag
and IP address are correct. See https://www.iana.org/assignments/bootp-dhcp-parameters/bootp-dhcp-parameters.xhtml for more info.

```

Dependencies
------------

NA

Example Playbook
----------------

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

