show-cpu-info
=============

This role checks the status of Intel Hyper-Threading (or AMD multithreading), and then reports detailed CPU information including the number of CPUs, virtual CPUs (vCPUs), and the CPU model. The role sets a fact indicating whether Hyper-Threading is enabled or disabled based on the number of threads per core.

## Tasks

### Check Intel Hyper-Threading (AMD Multithreading)

Sets a fact to determine if Hyper-Threading is enabled based on the number of threads per core.

`set_fact` Sets the hyper_threading_status fact. 

hyper_threading_status: A string indicating whether Hyper-Threading is enabled or disabled.

Condition checks if the number of threads per core is greater than 1 than Hyper-Threading is enabled.

### Show CPU Information

Displays detailed CPU information including the number of CPUs, vCPUs, CPU model, and Hyper-Threading status.

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
