# 7 Days to Die
7 Days to Die dedicated server.

## [Requirements][i]
Requires [r_pufky.game][g] galaxy-ng collection. See
[reference documentation][h] for troubleshooting and config variables.

  Resource | Minimum | Recommended
 ----------|---------|-------------
  CPU      | 2c/4t   | 4c/8t @3.0Ghz
  RAM      | 6GB     | 12GB
  Disk     | 16GB    | 20GB

## Role Variables
Detailed variable use documented in defaults. See usage for role operation.

* [defaults][j] - User configurable options.

* [ports][k] - Ports are **not** managed (defined for external use).

## Usage

### Feature Flags
Tasks are gated by feature flags and executed in the following order.

  Step | Flag                         | Notes
 ------|------------------------------|-------
  1    | seven_days_to_die_flg_update | Update server on launch or if already installed.
  2    | seven_days_to_die_flg_backup | Enable local scheduled backup.

### Example Playbooks

#### Default Server

``` yaml
- name: 'Configure a default 7 Days to Die server with backups.'
  ansible.builtin.include_role:
     name: 'r_pufky.game.satisfactory'
  vars:
    satisfactory_flg_backup: true
```

#### Custom Server
Configuration files will be interpreted as templates, allowing for vault use of
server configuration files. Files in this directory will be sync'ed to the
server. See [examples in files][n].

``` yaml
- name: 'Custom server with hot backups.'
  ansible.builtin.include_role:
     name: 'r_pufky.game.satisfactory'
  vars:
    satisfactory_flg_backup: true
    seven_days_to_die_cfg_backup_hot: true
    seven_days_to_die_cfg_server_config:
      'host_vars/7days.example.com/data/serverconfig.xml'
    seven_days_to_die_cfg_server_admin:
      'host_vars/7days.example.com/data/serveradmin.xml'
```

## Development
Configure [environment][a].

``` bash
# Run all tests.
molecule test --all
```

Testing variables:

  Variable          | type | Description
 -------------------|------|-------------
  url_inject_enable | bool | Disable **get_url** to inject files locally.

### [Releases][b]

  Release | Debian | Ansible | Notes
 ---------|--------|---------|-------
  2.x.x   | 13     | 2.20    | Ansible 2.20, feature flags, and semantic versioning.
  1.x.x   | 12     | 2.11    | Migration from private repository.

## Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License][c] | [direct link][f]

## Author Information
PGP: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9][d] | [github gist][e]


[a]: https://r-pufky.github.io/ansible_docs
[b]: https://semver.org/spec/v2.0.0
[c]: https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0
[d]: https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9
[e]: https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22

[f]: https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/LICENSE
[g]: https://github.com/r-pufky/ansible_collection_game
[h]: https://r-pufky.github.io/docs/games/seven_days_to_die
[i]: https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/meta/main.yml
[j]: https://github.com/r-pufky/ansible_seven_days_to_die/tree/main/defaults/main/main.yml
[k]: https://github.com/r-pufky/ansible_seven_days_to_die/blob/main/defaults/main/ports.yml
[n]: https://github.com/r-pufky/ansible_seven_days_to_die/tree/main/files