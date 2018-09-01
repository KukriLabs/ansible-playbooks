# KukriLabs Ansible Playbooks

Monorepo for KukriLabs Ansible Playbooks and Roles. Where possible (and appropriate) Docker is used in the installation of applications 

## Roles

Currently roles are only defined in the `roles/` directory and not available on Ansible Galaxy. Should there be a suitable demand for this functionality this is something we are open to providing.

### `prometheus-docker`

[Prometheus](https://prometheus.io/) monitoring system backed by [TimescaleDB](https://www.timescale.com/) running in Docker containers. 

### `grafana-docker`

[Grafana](https://grafana.com/) graphing system running in a docker container. Can be connected to docker network of `prometheus-docker` role (and others) to add Prometheus as a data source

## Playbooks

Playbooks provided are generally geared towards specific internal use cases but may be useful as a starting point or as reference examples.

## Setup

It is recommended to use [`pipenv`](https://pipenv.readthedocs.io/en/latest/) to create a new Python3 virtual environment and install the _exact dependencies_ for deterministic runs. An example workflow is shown below (assuming `pipenv` is installed):

```
$ # Create virtual environment as well as installing all dependencies of the project
$ pipenv install

$ # Activate virtual environment
$ pipenv shell

$ # Install any requirements for playbook
$ ansible-galaxy install -r requirements/{{ playbook_name }}.yml

$ # Run playbook (set up an inventory file as required)
$ ansible-playbook -i /path/to/inventory {{ playbook_name }}.yml
```

## Testing

### Vagrant

If [Vagrant](https://www.vagrantup.com/) is installed provided is a `Vagrantfile` which can be used to validate roles and playbooks using a similar workflow (using the `monitoring.yml` playbook) to the one below:

```
$ # Setup Pipenv environment

$ # Start vagrant
$ vagrant up

$ # Install ansible galaxy requirements
$ ansible-galaxy install -r requirements/monitoring.yml

$ # Run ansible playbook
$ ansible-playbook --check monitoring.yml \
    && ansible-playbook \
      -i ~/vagrant/ansible-playbooks/.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory monitoring.yml
```

Provided the Vagrant node private IP remains the same, Grafana should be available at `192.168.33.10:3000` and Prometheus at `192.168.33.10:9090`.

## License

See `LICENSE` file

## Copyright

Copyright (c) 2018 Ewan Jones of Kukri Labs
