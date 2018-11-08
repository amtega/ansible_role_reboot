# Ansible reboot role

This is an [Ansible](http://www.ansible.com) role which provides handlers to reboot machines.

See dependant roles documentation to know how to configure each one.

## Requirements

[Ansible 2.7+](http://docs.ansible.com/ansible/latest/intro_installation.html)

## Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Dependencies

[amtega.check_platform](https://galaxy.ansible.com/amtega/check_platform)

## Usage

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - amtega.reboot
  tasks:
    - name: create file and reboot
      copy:
        content: ""
        dest: /tmp/emptyfile1
        force: no
      notify:
        - reboot
        - reboot wait

    - meta: flush_handlers
```

The role provides a set of useful handlers:

- `reboot host`: reboot the host
- `wait host`: wait until the host can be accessed (e.g., after reboot)

## Testing

Tests are based on docker containers. You can setup docker engine quickly using the playbook `files/setup.yml` available in the role [amtega.docker_engine](https://galaxy.ansible.com/amtega/docker_engine).

Once you have docker, you can run the tests with the following commands:

```shell
$ cd amtega.reboot/tests
$ ansible-playbook main.yml
```

## License

Copyright (C) 2018 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García.
