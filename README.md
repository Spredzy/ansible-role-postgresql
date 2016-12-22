# Ansible Role: PostgreSQL

Installs and configures PostgreSQL on a server.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: database
      become: yes
      roles:
        - role: Spredzy.postgresql

## Role Variables

This is the list of role variables. Examples are found below.

  * `postgresql_package_name`: Name of the package to install
  * `postgresql_service_name`: Name of the PostgreSQL service
  * `posrgresql_data_folder`: Path to the PostgreSQL data folder
  * `posrgresql_extra_packages`: Extra packages to install along side server
  * `posrgresql_admin_role_name`: PostgreSQL Administrator name
  * `posrgresql_databases`: List of databases to create
  * `posrgresql_users`: List of users to create
  * `posrgresql_settings`: Settings to write in postgresql.conf


## Dependencies

None.

## Example Playbook

```
- hosts: databases
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - { role: Spredzy.postgresql }
```

*Inside `vars/main.yml`*:

```
---
postgresql_databases:
  db1:

postgresql_users:
  user1:
    db: db1
    password: password
    priv: "ALL"

postgresql_settings:
  listen_addresses = "'*'"
```

## License

Apache 2.0

## Author Information

Yanis Guenane <yanis+ansible@guenane.org>



