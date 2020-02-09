Role Name
=========

syslog: Syslog

[![Build Status](https://travis-ci.org/cmihai-ansible/syslog.svg?branch=master)](https://travis-ci.org/cmihai-ansible/syslog)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.syslog](https://galaxy.ansible.com/devopstoolbox.syslog)

```bash
ansible-galaxy install devopstoolbox.syslog
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
syslog_packages_state: present
syslog_remove_packages: true
syslog_enable_service: true
syslog_enable_selinux: true
syslog_copy_templates: true
syslog_firewall_configure: true
syslog_firewall_rules:
  - service: ssh
  - port: 3389
syslog_users:
  - user: devops
    group: docker
syslog_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install syslog on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: syslog is configured
      import_role:
        name: devopstoolbox.syslog
      vars:
        syslog_packages_state: present
        syslog_remove_packages: true
        syslog_enable_service: true
        syslog_enable_selinux: true
        syslog_copy_templates: true
        syslog_firewall_configure: true
        syslog_firewall_rules:
          - service: ssh
          - port: 3389
        syslog_users:
          - user: devops
            group: docker
        syslog_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: syslog
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
