# Ansible Role: docker_makemkv

An Ansible role to deploy MakeMKV application as [container](https://github.com/jlesage/docker-makemkv). Thanks to Jocelyn Le Sage for this!

## Requirements

used modules:
  - [docker_container](https://docs.ansible.com/ansible/latest/modules/docker_container_module.html)
  - [docker_image](https://docs.ansible.com/ansible/latest/modules/docker_image_module.html)
  - [docker_network](https://docs.ansible.com/ansible/latest/modules/docker_network_module.html)
  - [fail](https://docs.ansible.com/ansible/latest/modules/fail_module.html)

Fedora RPM packages:
  - python3-docker

## Installation

Install from [Github](https://github.com/donvipre/ansible-role-docker_makemkv)
```
git clone https://github.com/donvipre/ansible-role-docker_makemkv.git ansible-role-docker_makemkv
```

## Role variables

```
---
# defaults file for ansible-role-docker_makemkv

makemkv_name: makemkv
makemkv_image: jlesage/makemkv
makemkv_timezone: Etc/UTC
makemkv_display_width: "1280"
makemkv_display_height: "768"
makemkv_published_ports:
  - "5800:5800"
makemkv_network: makemkv
makemkv_iprange: 10.1.1.0/24
makemkv_volumes:
  - "/docker/appdata/makemkv:/config:rw"
  - "{{ lookup('env','HOME') }}:/storage:ro"
  - "{{ lookup('env','HOME') }}/HandBrake/output:/output:rw"
makemkv_devices: []

makemkv_supported_tasks:
  - install
  - uninstall
```

## Dependencies

None.

## Example Playbook

```
- hosts: servers
  roles:
    - { role: ansible-role-docker_makemkv, run_tasks: install }
```

## License

This work is licensed under [BSD-3-Clause](./LICENSE)

## Author Information

- Author: Uwe Arnold
- Mail: [donvipre@gmail.com](mailto:donvipre@gmail.com)
