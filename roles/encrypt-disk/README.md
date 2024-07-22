encrypt-disk
============

This Ansible role installs the necessary package, generates an RSA private key, encrypts a specified disk, formats it, and mounts it to a specified mount point. It uses LUKS (Linux Unified Key Setup) for encryption and ext4 for the filesystem.

## Tasks

### Install cryptsetup

Installs the `cryptsetup` package which is required for disk encryption.

### List All Disks and Their Size

Lists all disks along with their sizes, filtering to show only non-removable disks that match the specified `second_disk`.

`loop:` Iterates over all devices and `when:` Filters to non-removable disks matching `second_disk`

### Check RSA Private Key Exists

Checks if the RSA private key file exists one the host and registers the result in `luks_key_exist`

### Generate RSA Private Key (Skipping if Already Exists)

Generates an RSA private key on the host. Runs the task only if the key does not exist.

### Encrypt Disk

Encrypts the disk using LUKS using keyfile

### Format the Encrypted Disk

Formats the encrypted disk with the ext4 filesystem.

### Mount the Encrypted Disk

Mounts the encrypted and formatted disk to the specified mount point.

Role Variables
--------------

`second_disk` variable must be specified

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
