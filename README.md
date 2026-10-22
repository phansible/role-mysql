# Phansible Role: MySQL

[![CI](https://github.com/phansible/role-mysql/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-mysql/actions/workflows/ci.yml)

An Ansible Role that installs [MySQL](https://www.mysql.com/) 8.4 LTS on Ubuntu and Debian specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04 or 26.04, or Debian 12 or 13.
- Ansible 2.15 or newer.
- The `ansible.mysql` collection (bundled with the `ansible` package, or `ansible-galaxy collection install ansible.mysql`).
- Internet access to `repo.mysql.com`. MySQL comes from Oracle's official apt repository (`mysql-8.4-lts`) on every platform, since Debian only ships MariaDB.

## Role Variables

All variables live under one `mysql` dictionary in `defaults/main.yml`. Override the whole dictionary, since Ansible does not merge dictionaries by default.

| Variable | Default | Description |
| --- | --- | --- |
| `mysql.root_password` | `root` | Password set on the `root` accounts (`localhost`, `127.0.0.1`, `::1` and the machine hostname). |
| `mysql.database` | `phansible` | Database to create. |
| `mysql.user` | `changme` | User created with all privileges on `database`. |
| `mysql.password` | `changme` | Password for `user`. |
| `mysql.dump` | `""` | SQL file under `/vagrant/` imported into `database`. Empty skips the import. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    mysql:
      root_password: secret
      database: app
      user: app
      password: secret
      dump: ""
  roles:
    - role-mysql
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-mysql/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-mysql/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
