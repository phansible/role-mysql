# Phansible Role: MySQL

[![Build Status](https://travis-ci.org/phansible/role-mysql.svg?branch=master)](https://travis-ci.org/phansible/role-mysql)

An Ansible Role that installs [MySQL](https://www.mysql.com/) on Ubuntu specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

// TODO

## Role Variables

The default role variables are located in `defaults/main.yml` and provide information to allow the role to execute the commands successfully.

`root_password`: The root password for the MySQL `root` user, this is required due to the fact that a privileged account is required to create databases, uses, and set user privileges.

`user`: The name of the user this task will be creating.

`password`: The password for the created user.

`databases`: A list of databases this task will create. Each database in the list allows you to provide a database and dump value. This enables the setup of multiple databases and multiple imports. In YAML, each list item will start with a hyphen. For example, if we wanted to add another database to this role, it would look similar to this:

```yml
mysql:
    root_password: <your password>
    user: <username>
    password: <user's password>
    databases:
      - database: phansible
        dump: ""
      - database: my-app
        dump: "my-app.sql"
```

## Dependencies

// TODO

## Example Playbook

// TODO

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-mysql/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-mysql/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
