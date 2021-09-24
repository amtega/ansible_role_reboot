# Ansible reboot role

This is an [Ansible](http://www.ansible.com) role which provides handlers to reboot machines.

## Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Handlers

The role provides the following handlers to manage the host reboot:

- `reboot host`: reboot the host
- `wait host`: wait for the host to be rebooted

## Usage

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - amtega.reboot
  tasks:
    - name: Create file and reboot
      copy:
        content: ""
        dest: /tmp/emptyfile1
        force: no
      notify:
        - reboot
        - reboot wait

    - meta: flush_handlers
```

## Testing

Tests are based on [molecule with docker containers](https://molecule.readthedocs.io/en/latest/installation.html).

```shell
cd amtega.reboot

molecule test --all
```

## License

Copyright (C) 2021 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García.
