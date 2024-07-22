rename-interface
================

This role installs a Netplan configuration template, applies the configuration, and provides debugging information about the network interface. It uses a template file `int.j2` to configure network settings and ensures that the changes are applied immediately.

## Tasks

### Install Netplan Template and Apply Config

Installs the Netplan configuration from a template file `int.j2` and applies the configuration.

notify: Triggers the `netplan-apply` handler to apply the configuration.

register: Registers the result of the task in `command_result`.

### Show Interface Information

Displays information about the network interface if the previous task did not fail

Condition runs the task only if the previous task did not fail using `command_result`

## Jinja template

File: `int.j2` is the template file used for configuring the network interface.

It matches the interface by its mac address discovered in `ansible_facts`

Role Variables
--------------

`interface_name` is the new name of the interface. variable must be specified.

Dependencies
------------

Example Playbook
----------------

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
