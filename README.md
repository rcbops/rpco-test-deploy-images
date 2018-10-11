# README
This set of playbooks launches an MNAIO environment on Phobos using
pre-existing images from the Rackspace CDN.

It assumes that authorization credentials have already been loaded into the
environment.

The desired rpc-openstack branch to be used for the deploy **must** be entered
as an ansible variable at the time the playbooks are executed.

## Example usage
The examples below assume that your current working directory is the same as
this README file.

### First run
The primary use of the playbooks is to provision an instance on Phobos and
deploy the specified rpc-openstack MNAIO environment to that instance.
```
ansible-playbook playbooks/main.yml -e branch=queens
```

### Run on existing host
If you have an existing host, or one of the playbooks within this suite has
failed and you wish to execute the playbooks in isolation, you should provide
the path to the appropriate inventory file.
```
ansible-playbook -i inventory/hosts playbooks/pre_deploy.yml -e branch=queens
```

## TODO
Make hostname dynamic
