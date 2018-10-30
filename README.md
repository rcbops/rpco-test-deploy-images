# README
This set of playbooks launches an MNAIO environment on Phobos using
pre-existing images from the Rackspace CDN.

It assumes that openstack authorization credentials for your Phobos account
have already been loaded into your environment.

## Required variables
These playbooks assume that the following variable are declared. These should
be entered on the command-line.

* **keyname**: The name of the Openstack ssh key you would like deployed to
  the instance that is created on Phobos.  Setting this variable is mandatory
  and the playbook run will fail if it is not provided.
* **branch**: The branch of the rpc-openstack repo to use for the deploy.  This
  is used to determine the release number to fetch from the CDN.  This value
  will default to `master` if it is not declared.
* **prefix**: The prefix for the server instance created on Phobos.  The
  instance name created will be in the format `<prefix>-image-<branch>`.  This
  value will be set to a random number seeded by the inventory hostname if it
  is not declared.

## Example usage
The examples below assume that your current working directory is the same as
this README file.

### First run
The primary use of the playbooks is to provision an instance on Phobos and
deploy the specified rpc-openstack MNAIO environment to that instance.
```
ansible-playbook playbooks/main.yml -e prefix=jrd_20181031 -e keyname=mykey -e branch=queens
```

### Run on existing host
If you have an existing host, or one of the playbooks within this suite has
failed and you wish to execute the playbooks in isolation, you should provide
the path to the appropriate inventory file.
```
ansible-playbook -i inventory/hosts playbooks/pre_deploy.yml -e branch=queens
```
