# 7 Days to Die
7 Days to Die installation from steamcmd.

## Requirements
[supported platforms](https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/meta/main.yml)

## Role Variables
[defaults](https://github.com/r-pufky/ansible_seven_days_to_die/tree/main/defaults/main)

### Ports
All ports and protocols have been defined for the role.

[defaults/ports.yml](https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/defaults/main/ports.yml)

## Dependencies
**galaxy-ng** roles cannot be used independently. Part of
[r_pufky.game](https://github.com/r-pufky/ansible_collection_game) collection.

## Example Playbook
Read defaults documentation.

The following example will get an instance quickly up and running. Server will be created using the
steamcmd user from `r_pufky.game.steam`.
``` yaml
- name: '7 Days to Die server'
  hosts: '7days.example.com'
  become: true
  roles:
     - 'r_pufky.game.seven_days_to_die'
  vars:
    seven_days_to_die_srv_backup_enable: true
    seven_days_to_die_web_dashboard_enabled: true
    seven_days_to_die_cfg_server_admin_enable: true
    seven_days_to_die_cfg_server_admins:
      - platform: 'Steam'
        comment: 'Grant steam player root access'
        id: 76561198021925107
        level: 0
    seven_days_to_die_cfg_whitelist:
      - platform: 'Steam'
        id: 76561198021925107
    seven_days_to_die_cfg_api_tokens:
      - name: 'test'
        secret: 'test'
        level: 0
```

Changes updating the configuration only can be done to speed role application:
``` bash
ansible-playbook site.yml --tags 7days -e 'conan_exiles_srv_update_server=false'
```

## Development
Configure [environment](https://github.com/r-pufky/ansible_collection_game/blob/main/docs/dev/environment/README.md)

Run all unit tests:
``` bash
molecule test --all
```

### Releases
Release format: **{OS}-{SERVICE}-{ROLE}**

Each type inherits the versioning system used; defaulting to schematic
versioning.

`12.0.0-2.0.3-1.0.0`

* 12.0.0 - Debian 12 (bookworm).
* 2.0.3 - Service/app version.
* 1.0.0 - Role version.

Releases are branched on Debian releases:

* **[13.x.x](https://github.com/r-pufky/ansible_seven_days_to_die)**: 13 Trixie.
* **[12.x.x](https://github.com/r-pufky/ansible_seven_days_to_die/tree/12.x)**: 12 Bookworm.

## Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0)
 [(direct link)](https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/LICENSE)

## Author Information
PGP Fingerprint: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9](https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9)
| [github gist](https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22)
