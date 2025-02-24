# Repositories

## Description

This role simply configure repositories for client hosts.

## Instructions

Repositories are set in **repositories** variable. Two shapes are available: a
simple one and an advanced one.

Simple one:

```yaml
repositories:
  - os
  - bluebanquise
  - myrepo
```

Advanced one, to be combined with simple one as desired:

```yaml
repositories:
  - os
  - bluebanquise
  - name: epel
    baseurl: 'https://dl.fedoraproject.org/pub/epel/$releasever/$basearch/'
    proxy: 'https://proxy:8080'
```

Available advanced variables are:

* name
* baseurl
* enabled
* exclude
* gpgcheck
* gpgkey
* proxy
* state

Repository static path is computed using variables defined in the equipment group.

```yaml
ep_operating_system:
  distribution: centos # centos, redhat, debian, ubuntu, opensuse, etc.
  distribution_major_version: 8
  # Optional: define a minor distribution version to force (repositories/PXE)
  #distribution_version: 8.0
  # Optional: add an environment in the repositories path (eg. production, staging) (repositories/PXE)
  #repositories_environment: production
```

If equipment_profile is:

```yaml
ep_operating_system:
  distribution: centos
  distribution_major_version: 8
```

Then path will be: repositories/centos/8/$basearch/

If equipment_profile is:

```yaml
ep_operating_system:
  distribution: centos
  distribution_major_version: 8
  distribution_version: 8.1
```

Then path will be: repositories/centos/8.1/$basearch/

If equipment_profile is:

```yaml
ep_operating_system:
  distribution: centos
  distribution_major_version: 8
  distribution_version: 8.1
  repositories_environment: production
```

Then path will be: repositories/production/centos/8.1/$basearch/

For CentOS, the role will disable the default repositories of the distribution.
If one want to keep the distro repositories, they must define
`repositories_client_disable_distro_repos: False` in their inventory.

## Changelog

* 1.3.3: Support gpgkey for Ubuntu. Giacomo Mc Evoy <gino.mcevoy@gmail.com>
* 1.3.2: Flush handlers at the end of role repositories_client. #sla31
* 1.3.1: Updated SUSE subtask to handle missing repo definition when repo is a dictionary. Neil Munday <neil@mundayweb.com>
* 1.3.0: Update to pip Ansible. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.2.0: Add OpenSuSE support and correct ansible warning for included tasks loop. Neil Munday <neil@mundayweb.com>
* 1.1.3: Improve Ubuntu support. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.1.2: Incorporated fix for issue 534. Neil Munday <neil@mundayweb.com>
* 1.1.1: Adapt role to handle multiple distributions. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.1.0: Add Ubuntu support. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.0.8: Add state parameter. Bruno Travouillon <devel@travouillon.fr>
* 1.0.7: Simplified version of the role. Benoit Leveugle <benoit.leveugle@gmail.com>
* 1.0.6: Deprecate external_repositories. Bruno Travouillon <devel@travouillon.fr>
* 1.0.5: Added support for excluding packages from CentOS and RHEL repositories. Neil Munday <neil@mundayweb.com>
* 1.0.4: Clean. johnnykeats <johnny.keats@outlook.com>
* 1.0.3: Add support of major release version. Bruno <devel@travouillon.fr>
* 1.0.2: Added Ubuntu 18.04 compatibility. johnnykeats <johnny.keats@outlook.com>
* 1.0.1: Documentation. johnnykeats <johnny.keats@outlook.com>
* 1.0.0: Role creation. Benoit Leveugle <benoit.leveugle@gmail.com>
