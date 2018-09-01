
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

```
$ ansible-playbook --check analytics.yml \
    && ansible-playbook \
      -i ~/vagrant/ansible_playground/.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory analytics.yml
```