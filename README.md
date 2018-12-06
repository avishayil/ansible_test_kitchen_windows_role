
ansible_test_kitchen_windows_role
=========
This role is an example role for using `test-kitchen` on ansible roles that is meant to run on Windows hosts.
We use AWS EC2 to deploy the machines, 

Role Tasks
--------------
- **main** - Downloading and Installing Google Chrome on the target machine.

Role Variables
--------------

- This role does not require any variables.

Outputs
------------
- This role has no outputs.

Dependencies
------------
- This role does not have any dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    # Assuming that you have some machines in 'jmeter' hosts group
    - hosts: tag_kitchen_type_windows
      gather_facts: no
      tasks:      
        - include_role:
            name: ansible_test_kitchen_windows_role

Testing
-------
We use [Test-Kitchen](https://github.com/test-kitchen/test-kitchen) for testing ansible roles that was meant to run on Windows hosts.

- Install [ChefDK](https://downloads.chef.io/chefdk)
- Install `chef` gems:
  * `$ chef gem install 'kitchen-ansible'`
  * `$ chef gem install 'winrm'`
  * `$ chef gem install 'winrm-fs'`
  * `$ chef gem install 'kitchen-pester'`
- Copy `.kitchen.yml` to `.kitchen.local.yml`, edit and override per your needs (instance profile, subnet, keypair, etc).
- Run `$ kitchen create` and take note of the windows machine that was created.
- Make sure that the following files are executable (by running `chmod +x file`):
  * `$ chmod +x inventory/generate_inventory.sh`
  * `$ chmod +x inventory/ec2.py`
- Update the hosts file on the ansible inventory running `$ ./inventory/generate_inventory.sh` from the root of the repository
- Run `$ kitchen converge` to run the default playbook from the provisioned ansible machine on the windows host.
- Run `$ kitchen verify` for running pester tests.
- Run `$ kitchen destroy` to terminate instances.

Todo
-------


License
-------

BSD

Author Information
------------------

Avishay Bar,
Cloud Initiatives team,
CyberArk 2018