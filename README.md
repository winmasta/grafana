Role Name
=========

Ansible role for latest grtafana in docker container. UI behind nginx with basic authorization. Tested on:
  - Ubuntu 14.04 Trusty
  - Ubuntu 16.04 Xenial

Requirements
------------

Installed OS:
 - Ubuntu 14.04 Trusty
 - Ubuntu 16.04 Xenial

Role Variables
--------------

GRAFANA_DIR: /var/lib/grafana # Grafana persistent data directory
GRAFANA_PORT: 3000 # Grafana default UI port

Dependencies
------------

Depends on:
 - winmasta.docker-latest
 - winmasta.nginx

License
-------

MIT
