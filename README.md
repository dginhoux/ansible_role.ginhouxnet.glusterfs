Ansible Role : dginhoux.glusterfs
=========

This ansible role configure glusterfs server


Requirements
------------

This role require a supported platform defined in `meta/main.yml`.
It will skip node with unsupported platform ; this behaviour can be bypassed by settings this variable `asserts_bypass=True`.


Role Variables
--------------

Necessary variables are defined on `defaults/main.yml`.

The variable `gluster_node_peer_address` need to be defined on each host (host_vars).


Dependencies
------------

none

Example Playbook
----------------



License
-------

BSD


Author Information
------------------

https://github.com/dginhoux/
