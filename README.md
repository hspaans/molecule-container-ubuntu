# Ubuntu Container for Molecule

An [Ubuntu][ubuntu] based container image for testing [Ansible][ansible] Roles with [Molecule][molecule]. The [repository][docker-ubuntu2004-ansible] from [Jeff Geerling][geerlingguy] was taken as starting point to create the repository.

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Ubuntu 20.04 (Focal).

```yml
---
dependency:
  name: galaxy
driver:
  name: docker
lint: |
  set -e
  yamllint .
  ansible-lint
  flake8
platforms:
  - name: instance
    image: "ghcr.io/hspaans/molecule-container-ubuntu:20.04"
    command: ""
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true
    pre_build_image: true
provisioner:
  name: ansible
verifier:
  name: testinfra
```

## Versions

The container is based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) distribution versions with official support and fall within N and N-1. The *latest*-tag is an experimental tag to test future releases.

| Platform | Version        | Image                                                                        |
|:--------:|:--------------:|:----------------------------------------------------------------------------:|
| Ubuntu   | 18.04 (Bionic) | [hspaans/molecule-container-ubuntu:18.04][molecule-container-ubuntu:18.04]   |
| Ubuntu   | 20.04 (Focal)  | [hspaans/molecule-container-ubuntu:20.04][molecule-container-ubuntu:20.04]   |
| Ubuntu   | 21.04 (Hirsute) | [hspaans/molecule-container-ubuntu:latest][molecule-container-ubuntu:latest] |

[ansible]: https://github.com/ansible/ansible
[docker-ubuntu2004-ansible]: https://github.com/geerlingguy/docker-ubuntu2004-ansible
[geerlingguy]: https://github.com/geerlingguy
[molecule]: https://github.com/ansible-community/molecule
[molecule-container-ubuntu:latest]: ghcr.io/hspaans/molecule-container-ubuntu:latest
[molecule-container-ubuntu:18.04]: ghcr.io/hspaans/molecule-container-ubuntu:18.04
[molecule-container-ubuntu:20.04]: ghcr.io/hspaans/molecule-container-ubuntu:20.04
[ubuntu]: https://ubuntu.com/
