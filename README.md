ansible_role_proxmox_offline_guest_power_on
===========================================

This role relies on Proxmox API and the qemu-guest-agent. On a defined number of VMIDs, it power-on any offline guest.  
After a defined number of minutes, the role will shut down previously stopped guests.  
This can be used to run updates on offline guests during off hours for example.

Requirements
------------

The qemu-guest-agent is mandatory on any guest targeted by the playbook. It is used to turn on/off offline guests.  
All tasks are using Proxmox API, you can run the playbook on localhost only.


Defaults Variables
------------------

pve_vm_ids: List all vmids here. It has to be a list because the role will loop into each id. You can use multiple range.
```
  - "{{ range(100, 160) | map('string') | list }}"
  - "{{ range(200, 880) | map('string') | list }}"
  - 999  
```
delay_time: Delay until the role start powering off vm previously stopped. Delay time is in minutes.

Vars Variables
--------------

All API login info are in there.  
It's using the API token authentication process. You have to provide the user id, user token id and secret.
 
Example Playbook
----------------

    - hosts: localhost
      vars:
        pve_vm_ids:
          - "{{ range(100, 160) | map('string') | list }}"
          - 888
        delay_time: 60
      roles:
         - victorsierra314.ansible_role_proxmox_offline_guest_power_on

License
-------

BSD

Author Information
------------------

I have been working with Proxmox for quite some time now. Took me some time to get to gibhut but I'm glad I can share what I have build along the year. Enjoy.
