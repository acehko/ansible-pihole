# Ansible Role: Pi-hole
[![Build Status](https://travis-ci.com/acehko/ansible-pihole.svg?branch=master)](https://travis-ci.com/acehko/ansible-pihole)

Ansible role for running Pi-hole on docker.

## Requirements
> You can all of the requirements with the [acehko.docker](https://github.com/acehko/ansible-docker) role.

- Docker
- Docker Compose
- Docker Python package

## Variables
| Variable             | Default                       | Description                                                                                                |
|:---------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------|
| **pihole_dir**       | `/etc/docker/projects/pihole` | The directory where the docker compose file will be copied.                                                |
| **pihole_name**      | `pihole`                      | The docker compose project name. Docker containers, volumes and networks will be prefixed with this value. |
| **pihole_image**     | `pihole/pihole:v4.4`          | Pi-hole docker image. If changed the role may not work correctly.                                          |
| **pihole_host_mode** | `false`                       | Whether to run the container with `network_mode=host`.                                                     |
| **pihole_env**       |                               | Environment variables for the Pi-hole container.                                                           |

## Dependencies
None.

## Example Playbook
```yaml
- hosts: all
  roles:
    - role: acehko.pihole
      pihole_host_mode: true
      pihole_env:
        TZ: Europe/Zagreb
        WEBPASSWORD: changeme
        DNS1: 1.1.1.1
        DNS2: 1.0.0.1
        ServerIP: 192.168.0.123
        VIRTUAL_HOST: pi.hole
        INTERFACE=eth0
```

## License
[MIT](LICENSE)

## Author Information
[Andrija Čehko](https://github.com/acehko)
