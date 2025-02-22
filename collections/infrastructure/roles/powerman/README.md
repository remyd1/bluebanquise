# Powerman

## Description

This role provides powerman, to manage nodes power via ipmi (BMC).

## Instructions

To power on node, use:

```
powerman --on bar,foo[7,9-10]
```

Refer to: https://linux.die.net/man/1/powerman

## Input

Mandatory inventory vars:

**hostvars[inventory_hostname]**

* icebergs_system

**hostvars[hosts]**

* ep_equipment_authentication.user
* ep_equipment_authentication.password
* bmc
   * .name
   * .ip4

## Output

Packages installed:

* powerman
* freeipmi

Files generated:

* /etc/powerman/powerman.conf

## Changelog

* 1.2.1: Fix error when ep_host_authentication does not contain IPMI credentials. Giacomo Mc Evoy <gino.mcevoy@gmail.com>
* 1.2.0: Update to pip Ansible. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.1.1: Fix bluebanquise-filters package name. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.1.0: Implement support for externaly defined BMC. johnnykeats <johnny.keats@outlook.com>
* 1.0.0: Role creation. Benoit Leveugle <benoit.leveugle@gmail.com>
