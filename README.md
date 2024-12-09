# Netdata Ansible

## Tested on

- Debian 12
- OpenSUSE 15.6

## Roles



`ansible-playbook -e "distro=stable" netdata-agent.yml`

Or you can set in on per host basis, using inventory file or hosts_var/hostname.

> purge.yml:

Removes both installed repository and the package, making efforts to remove all possible remains like the log or configuration files.

> claim.yml:

Claims the agent against Netdata Cloud

## Parameters

Playbooks behavior is parameterized to some extent. You may add or change the global settings in `group_vars/all` file or on per host basis in corresponding files in `host_vars/`
You might also want to set some parameters in inventory file, of course. Or directly in the command line. Examples:

`ansible-playbook --limit=debian10,ubuntu20 netdata-agent.yml`

`ansible-playbook -u toor --limit=rocky8 -e "distro=edge" purge.yml`

*Warning.*

You cannot just switch from stable to edge repos (nor visa versa). You have to purge existing installation first.

## To do

- The only agent configuration file used for the time being is `netdata.conf`. Perhaps, other configuration files handling should be added.
