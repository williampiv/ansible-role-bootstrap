# Ansible-Bootstrap

[![Build Status](https://travis-ci.org/williampiv/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.org/williampiv/ansible-role-bootstrap)

More to come here. This is a role for doing some basic boostrap magic, on a stock system (so not deployed with some fancy Kickstart or the like.)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    remote_ansible_user_key_location: 'sshkeys/ansible.pub'

This is the location of the public key for the ansible user. Ideally this is the public key that is paired to the private key ansible will use to connect via SSH to your hosts.

    remote_ansible_user: ansible

The name of the remote ansible user. Ideally, this user will have already been created (with bare-bones config) and Ansible will use this user to administer hosts.

    selinux_enable: true

Do you want Ansible to be successful in an SELinux environment? True or false. On Debian systems, this will install SELinux. If you hate SELinux, you can disable this, but you'll want to disable SELinux on EL systems (Centos/RHEL/Fedora) or Ansible may not work the way you want it to.

## Dependencies

If you are enabling the SSH lockdown, this role will not install an SSH server, and will therefore fail if this is enabled, but SSH is not installed.

## Example Playbook

    - hosts: all
      vars_files:
        - vars/main.yml
      roles:
        - williampiv.bootstrap

*Inside `vars/main.yml`*:

    remote_ansible_user_key_location: 'sshkeys/ansible.pub'
    remote_ansible_user: ansible
    selinux_enable: true

## License

GNU GPLv3

## Author Information

This role was created in 2020 by William Perdue
