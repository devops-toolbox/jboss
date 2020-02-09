Role Name
=========

jboss: Jboss

[![Build Status](https://travis-ci.org/cmihai-ansible/jboss.svg?branch=master)](https://travis-ci.org/cmihai-ansible/jboss)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.jboss](https://galaxy.ansible.com/devops-toolbox.jboss)

```bash
ansible-galaxy install devops-toolbox.jboss
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
jboss_packages_state: present
jboss_remove_packages: true
jboss_enable_service: true
jboss_enable_selinux: true
jboss_copy_templates: true
jboss_firewall_configure: true
jboss_firewall_rules:
  - service: ssh
  - port: 3389
jboss_users:
  - user: devops
    group: docker
jboss_selinux_booleans:
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
- name: Install jboss on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: jboss is configured
      import_role:
        name: devops-toolbox.jboss
      vars:
        jboss_packages_state: present
        jboss_remove_packages: true
        jboss_enable_service: true
        jboss_enable_selinux: true
        jboss_copy_templates: true
        jboss_firewall_configure: true
        jboss_firewall_rules:
          - service: ssh
          - port: 3389
        jboss_users:
          - user: devops
            group: docker
        jboss_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: jboss
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
