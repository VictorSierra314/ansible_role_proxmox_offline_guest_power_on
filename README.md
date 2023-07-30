Role Name
=========

This role relies on Proxmox API and the qemu-guest-agent. On a defined number of VMIDs, it power-on any offline guest.
After a defined number of minutes, the role will shut down previously stopped guests.
This can be used to run updates on offline guests during off hours for example.

Requirements
------------

The qemu-guest-agent is mandatory on any guest targeted by the p^laybook. It is used to turn on/off offlines guests.
All tasks are using the Proxmox API, you can run the playbook on localhost only.


Defaults Variables
------------------

pve_vm_ids: List all vmids here. It has to be a list because the role will loop into each id. You can use multiple range.
  - "{{ range(100, 160) | map('string') | list }}"
  - "{{ range(200, 880) | map('string') | list }}"
  - 999
delay_time: Delay until the role start powering off vm previously stopped. Delay time is in minutes.

Vars Variables
--------------

All API login info are in there.
It's using the API token authentication process. You have to provide the user id, user token id and secret.
 
Example Playbook
----------------

    - hosts: localhost
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
