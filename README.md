ubuntu-preparation
==================

This playbook `prepare-ubuntu.yaml` configures various aspects of a Linux system, including disk encryption, network interface configuration, CPU power management, and performance tuning. Hosts are specified in `inventory` file.

 The playbook uses custom roles:

    - encrypt-disk - Implements the procedure of encrypting the second disk in the system

    - encrypt-partition - Implements a procedure to encrypt the partition that is present on the disk next to the root partition

    - rename-interface - Renames the active network interface

    - disable-c-state - Disables C-state for all available CPUs.

    - show-cpu-info - Displays list of CPUs and information about Intel Hyper-Threading (AMD multithreading)

 along with the role:

    - linux-system-roles.tuned - Switches CPU operation from power-saving mode to more productive mode

Variables
---------

### encrypt-disk

variable `second_disk` must be specified to encrypt the second disk in the system.

### encrypt-partition

variable `partition` must be specified to encrypt the partition next to root

### rename-interface

variable `interface_name` must be specified to rename the default host network interface to specified name

Dependencies
------------

Because Ansible doesnt provide module to use `tuned`. The role `linux-system-roles.tuned` must be installed from Ansible Galaxy:

```
ansible-galaxy role install linux-system-roles.tuned
```

variable: `profile` must be specified to configure tuned. Basic profiles that are available are balanced, powersave, throughput-performance, and latency-performance. More profiles may be available depending on OS version.

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
