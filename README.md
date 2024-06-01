Ansible Role: hostsfile
=========

Configures `/etc/hosts` on supported Linux distributions and `C:\Windows\System32\drivers\etc\hosts` on supported Windows versions. The hosts file contents are replaced with the content from specified variables. Any changes will result in a backup of the original file.

Supported Platforms
-------------------
- Enterprise Linux (Red Hat, CentOS, Alma Linux OS, Rocky Linux, Oracle Linux)
- Debian/Ubuntu
- Windows


Requirements
------------

This role depends on the `ansible.windows` collection. To install it, use:

```bash
ansible-galaxy collection install ansible.windows
```

Role Variables
--------------

Below is a list of available variables with their default values where applicable (see `defaults/main.yml`):

| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `hostsfile_add_default_ipv4` | No | true | Boolean. If true, adds default IPv4 entries. |
| `hostsfile_add_default_ipv6` | No | true | Boolean. If true, adds default IPv6 entries. |
| `hostsfile_backup` | No | true | Boolean. If true, creates a backup of the hosts file when modified. |
| `hostsfile_hosts_entries` | Yes | [] | List of host entries, each consisting of: `ip` (IP address), `name` (FQDN), `comment` (optional comment), `aliases` (optional list of aliases). |

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers

      vars:
        hostsfile_add_default_ipv4: true
        hostsfile_add_default_ipv6: false
        hostsfile_backup: true
        hostsfile_hosts_entries:
          - ip: 192.168.0.1
            name: examplehost1.local
            comment: hosts entry for examplehost1
            aliases:
              - examplehost1
              - example1
          - ip: 192.168.0.1
            name: examplehost2.local
            comment: hosts entry for examplehost2
            aliases:
              - examplehost2
              - example2

      roles:
        - role: hostsfile

License
-------

MIT

Author Information
------------------

Mattias Jonsson
