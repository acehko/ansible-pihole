# Ansible Role: Pi-hole
[![Build Status](https://travis-ci.com/acehko/ansible-pihole.svg?branch=master)](https://travis-ci.com/acehko/ansible-pihole)

Ansible role for running Pi-hole on docker. Only `host` network is supported.

## Requirements
> You can install all of the requirements with the [acehko.docker](https://github.com/acehko/ansible-docker) role.

- Docker
- Docker Compose
- Docker Python package

## Variables
| Variable                     | Default                       | Description                                                                                                |
|:-----------------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------|
| **pihole_dir**               | `/etc/docker/projects/pihole` | The directory where the docker compose file will be copied.                                                |
| **pihole_name**              | `pihole`                      | The docker compose project name. Docker containers, volumes and networks will be prefixed with this value. |
| **pihole_image**             | `pihole/pihole:v4.4`          | Pi-hole docker image. If changed the role may not work correctly.                                          |
| **pihole_network_mode**      | `host`                        | Network mode in which the Pi-hole should run. Only `host` is supported.                                    |
| **pihole_ip**                |                               | **Required**. Pi-hole ip address.                                                                          |
| **pihole_hostname**          | `pi.hole`                     | Hostname on which Pi-hole will be available.                                                               |
| **pihole_timezone**          | `UTC`                         | Pi-hole timezone.                                                                                          |
| **pihole_password**          | `changeme`                    | Password for the web interface.                                                                            |
| **pihole_dns**               | `[1.1.1.1, 1.0.0.1]`          | Array of Upstream DNS servers.                                                                             |
| **pihole_dhcp**              | `false`                       | Use Pi-hole as a DHCP server.                                                                              |
| **pihole_dhcp_start**        |                               | **Required if DHCP enabled** Start of DHCP ip range.                                                       |
| **pihole_dhcp_end**          |                               | **Required if DHCP enabled** End of DHCP ip range.                                                         |
| **pihole_dhcp_gateway**      |                               | **Required if DHCP enabled** Gateway (router) ip sent by the DHCP server.                                  |
| **pihole_dhcp_leasetime**    | `24`                          | DHCP lease time in hours.                                                                                  |
| **pihole_dhcp_domain**       | `lan`                         | Netowork domain name sent by the DHCP server.                                                              |
| **pihole_dhcp_rapid_commit** | `false`                       | Enable DHCPv4 rapid commit.                                                                                |

## Dependencies
None.

## Example Playbook
```yaml
- hosts: all
  roles:
    - role: acehko.pihole
      pihole_ip: 192.168.0.123
      pihole_dns: 
        - 8.8.8.8
        - 8.8.4.4
```

## License
[MIT](LICENSE)

## Author Information
[Andrija Čehko](https://github.com/acehko)
