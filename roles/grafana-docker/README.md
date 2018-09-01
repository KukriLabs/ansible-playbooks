Grafana Docker
=========

[Grafana](https://grafana.com/) graphing system running in a docker container.

Once installed Grafana is available on `:3000` (defined by variable `grafana_port`)

Requirements
------------

Docker to be installed on the inventory hosts. Recommended role [`geerlingguy.docker`](https://galaxy.ansible.com/geerlingguy/docker/). 

If wanting to use in combination with [Prometheus](https://prometheus.io/) monitoring it is suggested to use the provided `prometheus-docker` role.

Role Variables
--------------

See all variables defined in `defaults/main.yml` which can be overwritten as necessary. 

Dependencies
------------

- [`geerlingguy.docker`](https://galaxy.ansible.com/geerlingguy/docker/). 

Example Playbook
----------------

    - hosts: monitoring
      roles:
        - prometheus-docker
        - grafana-docker
      vars:
        # connect grafana to the docker network created by the prometheus-docker role
        grafana_additional_networks:
          - name: prometheus_frontend

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
