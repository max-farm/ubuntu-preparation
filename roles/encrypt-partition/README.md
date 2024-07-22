encrypt-partition
=================

This role installs the necessary package, generates an RSA private key if it does not already exist, encrypts a specified partition using LUKS, formats the encrypted partition, and mounts it to a specified mount point.

## Tasks

### Install cryptsetup

Installs the `cryptsetup` package which is required for disk encryption.

### Check RSA Private Key Exists

Checks if the RSA private key file exists one the host and registers the result in `luks_key_exist`

### Generate RSA Private Key (Skipping if Already Exists)

Generates an RSA private key on the host. Runs the task only if the key does not exist.

### Encrypt Partition

Encrypts the specified partition using LUKS.

`type:` Specifies the LUKS type (luks1) for using with partitions less than 16MB


Role Variables
--------------

`partition` variable must be specified

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

TBD
---
Automation for finding the partition next to root.