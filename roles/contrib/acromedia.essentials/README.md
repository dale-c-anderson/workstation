# essentials

![.github/workflows/molecule.yml](https://github.com/AcroMedia/ansible-role-essentials/workflows/.github/workflows/molecule.yml/badge.svg)

Install utilities commonly needed by sysadmins and developers

## Requirements

* Red Hat or Ubuntu

## Role Variables

* basic_packages_redhat (list)

  A list of packgaes to install on Red Hat / CentOS boxes. See defaults/main.yml.

* basic_packages_ubuntu (list)

  A list of packgaes to install on Ubuntu boxes. See defaults/main.yml.

* set_bash_history_timestamps (boolean)

  Not a package; just a tweak for bash shells that we find useful.

## Dependencies

None

## Example Playbook

    - hosts: servers
      roles:
         - { role: acromedia.essentials }

## License

AGPLv3

## Author Information

Acro Media Inc.
https://www.acromedia.com/
