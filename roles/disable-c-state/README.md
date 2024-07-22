disable-c-state
===============

Role ensures that the C-states configuration is correctly set in the GRUB configuration on a Linux system. The role will check if the C-states settings are present, set them if they are not. A system reboot will be performed to apply the changes.

To control over C-states, kernel parameter is set to `intel_idle.max_cstate=0` to disable intel_idle driver.

Parameter `processor.max_cstate=1` is set to enable maximum CPU perfomance, prevents the CPU from dropping into a sleep state when idle.

## Tasks:

### Check if C-States is Configured

- This task checks if the C-states parameters are already present in the GRUB configuration file.

  backrefs: Enables backreferences in the regular expression.
  path: Specifies the path to the GRUB configuration file.
  regexp: Defines the regular expression to find the line to modify.
  line: Sets the C-states parameters if not already present.
  when: Runs the task only if the parameters are not found.
  notify: Triggers the update_grub handler if changes are made.

### Set C-States 

- This task sets the C-states parameters in the GRUB configuration file if they are not already set. And reboot is performed af

  backrefs: Enables backreferences in the regular expression.
  path: Specifies the path to the GRUB configuration file.
  regexp: Defines the regular expression to find the line to modify.
  line: Sets the C-states parameters if not already present.
  when: Runs the task only if the parameters are not found.
  notify: Triggers the update_grub and reboot-host handlers if changes are made

### Show Current Boot Config

- This task displays the current boot configuration to the user.

### Update GRUB

This handler updates the GRUB configuration to apply the changes.

### reboot-host

This handler reboots the host, wait 30 seconds, attempt to connect via ssh and run whoami, disconnect after 5 seconds if ssh isnt working, keep attempting to connect for 10 minutes (600 seconds)

Requirements
------------

Role Variables
--------------

---

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

Prompts for auto rebooting the hosts
