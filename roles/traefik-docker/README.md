Traefik Docker
=========

[Traefik](https://traefik.io/) is a reverse proxy/router that supports service discovery via Docker and automatic SSL via Let's Encrypt (amongst many other features). By using this role in conjunction with other docker containers traffic can be automatically secured and routed.

We recommend using this role to protect traffic to our `grafana-docker` and/or `prometheus-docker` roles.

Requirements
------------

Docker to be installed on the inventory hosts. Recommended role [`geerlingguy.docker`](https://galaxy.ansible.com/geerlingguy/docker/). 

Role Variables
--------------

See all variables defined in `defaults/main.yml` which can be overwritten as necessary. 

Dependencies
------------

- [`geerlingguy.docker`](https://galaxy.ansible.com/geerlingguy/docker/)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

      - name: Install monitoring machine
        hosts: all
        roles:
          - role: geerlingguy.docker
            tags:
              - docker
          - role: prometheus-docker
            tags:
              - prometheus
          - role: grafana-docker
            tags:
            - grafana
          - role: traefik-docker
            tags:
            - traefik
        vars:
          grafana_traefik_enable: true
          grafana_additional_networks:
            - name: prometheus_frontend
          traefik_additional_networks:
            - name: grafana
          grafana_traefik_allowed_hosts:
            - 'grafana.example.com'
          grafana_traefik_frontend_rule: "Host: grafana.example.com"

License
-------

The MIT License (MIT)

Copyright (c) 2018 Ewan Jones of Kukri Labs

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Author Information
------------------

Ewan Jones for Kukri Labs

https://keybase.io/ejones
