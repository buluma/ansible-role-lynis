# [Ansible role lynis](#ansible-role-lynis)

Install and configure lynis on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-lynis/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-lynis/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-lynis/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-lynis)|[![downloads](https://img.shields.io/ansible/role/d/buluma/lynis)](https://galaxy.ansible.com/buluma/lynis)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-lynis.svg)](https://github.com/buluma/ansible-role-lynis/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-lynis/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  pre_tasks:
    - name: Update apt cache.
      apt: update_cache=yes cache_valid_time=600
      when: ansible_os_family == 'Debian'
      changed_when: false

  roles:
    - role: buluma.cron
    - role: buluma.git
    - role: buluma.lynis
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-lynis/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-lynis/blob/master/defaults/main.yml):

```yaml
---
# defaults file for lynis

# Where to install lynis
lynis_destination: "/tmp/lynis"

# The version to install
lynis_version: "3.0.6"

# Where to save the output of a report.
lynis_output: "{{ lynis_destination }}/{{ ansible_date_time.date }}-audit_system.txt"

# Run lynis on execution of the playbook?
lynis_run_now: true

# Schedule a repetetive job?
lynis_cronjob: true
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-lynis/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.cron](https://galaxy.ansible.com/buluma/cron)|[![Build Status GitHub](https://github.com/buluma/ansible-role-cron/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-cron/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-cron/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-cron)|
|[buluma.git](https://galaxy.ansible.com/buluma/git)|[![Build Status GitHub](https://github.com/buluma/ansible-role-git/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-git/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-git/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-git)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-lynis/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Amazon](https://hub.docker.com/r/buluma/amazonlinux)|all|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|
|[Kali](https://hub.docker.com/r/buluma/kalilinux)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-lynis/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-lynis/blob/master/LICENSE).

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)

