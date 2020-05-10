# Ansible Role: Pi-hole
[![Build Status](https://travis-ci.com/acehko/ansible-pihole.svg?branch=master)](https://travis-ci.com/acehko/ansible-pihole)

Ansible role for running Pi-hole on docker.

## Requirements
> You can all of the requirements with the [acehko.docker](https://github.com/acehko/ansible-docker) role.

- Docker
- Docker Compose
- Docker Python package

## Variables
| Variable         | Default                       | Description                                                                                                                    |
|:-----------------|:------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| **project_dir**  | `/etc/docker/projects/pihole` | The directory where the docker compose file will be copied.                                                                    |
| **project_name** | `pihole`                      | The docker compose project name. Docker containers, volumes and networks will be prefixed with this value.                     |
| **image**        | `pihole/pihole:v4.4`          | Pi-hole docker image. If changed the role may not work correctly.                                                              |
| **ip**           |                               | **Required**. Pi-hole ip address.                                                                                              |
| **hostname**     | `pi.hole`                     | Pi-hole hostname.                                                                                                              |
| **env**          |                               | Environment variables for the Pi-hole container. `ServerIP` and `VIRTUAL_HOST` are set with the `ip` and `hostname` variables. |

## Dependencies
None.

## Example Playbook
```yaml
- hosts: all
  roles:
    - role: acehko.pihole
      ip: 192.168.0.123
      hostname: pihole.local
      env:
        TZ: Europe/Zagreb
        WEBPASSWORD: changeme
        DNS1: 1.1.1.1
        DNS2: 1.0.0.1
```

## License
[MIT](LICENSE)

## Author Information
[Andrija Čehko](https://github.com/acehko)
