Ansible Role: ansible_role_hostsfile
=========

An Ansible role that configures /etc/hosts on supported Linux distributions and C:\Windows\System32\drivers\etc\hosts on supported Windows versions. The contents of the hosts file is replaced with content from variables. Any modifications will result in a backup of original file, the backed up file will have a name in the format of hosts.\<int>.\<timestamp>~.
This role supports the following OS/Linux distributions:

<ul>
<li>CentOS 7/8
<li>Red Hat Enterprise Linux 7/8
<li>Ubuntu 18/20/22
<li>Windows Server 2012r2, 2016, 2019, 2022
</ul>

Requirements
------------

This role is dependent on the ansible.windows collection.
To install it, use: ansible-galaxy collection install ansible.windows.

Role Variables
--------------

Available variables are listed below, along with default values where applicable (see defaults/main.yml):

    ansible_role_hostsfile_add_default_ipv4: true

Boolean, if set to true to add default IPv4 entries.  

    ansible_role_hostsfile_add_default_ipv6: true

Boolean, if set to true add default ipv6 entries.  

    ansible_role_hostsfile_backup: true

Boolean, if set to true create a backup of the hosts file when modifed.   

    ansible_role_hostsfile_hosts_entries: []

List of host entries consisting of the following variables:

    ip 

IP address of the host entry.  

    name
    
FQDN of the hosts entry.  

    comment

Optional, comment to be added to the entry.  

    alias 
    
Optional, aliases to be added to the hosts entry.  


Dependencies
------------

This role has no dependencies on other roles.

Example Playbook
----------------

    - hosts: servers

      vars:
        ansible_role_hostsfile_add_default_ipv4: true
        ansible_role_hostsfile_add_default_ipv6: false
        ansible_role_hostsfile_backup: false
        ansible_role_hostsfile_hosts_entries:
        - ip: 1.2.3.4
            name: examplehost.local
            comment: added to provide access to examplehost
            aliases:
            - examplehost
            - example1

            roles:
                - role: ansible_role_hostsfile

License
-------

MIT

Author Information
------------------

Mattias Jonsson
