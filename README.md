# ansible-role-joinaddomain
Ansible role to join Linux machine to Active Directory domain

## Variables needed are:
```
ad_domain:
ad_domain_user:
ad_domain_pass:
ad_ssh_users: []
ad_ssh_groups: []
```

ad_ssh_users and ad_ssh_groups relate to AD account/groups that you would like to have ssh and sudo access, can be a list.
The playbook will generate a file under /etc/sudoers.d/ named after each user and group to grant sudo access.

You can override the variables under /defaults/main.yml or simply copy them to a `/host_vars/<hostname>.yml` file or `/group_vars/all.yml` file.

## Example playbook
`playbook.yml`
```
- hosts: all
  become: true
  vars_files:
    - ad.yml
  roles:
    - ansible-role-joinaddomain
```
```
ad.yml
---
ad_domain: "example.com"
ad_domain_user: "administrator"
ad_domain_pass: "password123"
ad_ssh_users: []
ad_ssh_groups: [Domain Admins]
```

## OS Tested
- Ubuntu 20.04
