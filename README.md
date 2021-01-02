# Ubuntu Container for Molecule

An [Ubuntu][ubuntu] based container image for testing [Ansible][ansible] Roles with [Molecule][molecule].

## Example

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
| Ubuntu   | 20.10 (Groovy) | [hspaans/molecule-container-ubuntu:latest][molecule-container-ubuntu:latest] |

[ansible]: https://github.com/ansible/ansible
[molecule]: https://github.com/ansible-community/molecule
[molecule-container-ubuntu:latest]: ghcr.io/hspaans/molecule-container-ubuntu:latest
[molecule-container-ubuntu:18.04]: ghcr.io/hspaans/molecule-container-ubuntu:18.04
[molecule-container-ubuntu:20.04]: ghcr.io/hspaans/molecule-container-ubuntu:20.04
[ubuntu]: https://ubuntu.com/
