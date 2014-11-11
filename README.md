Role Name
=========

Ansible role to set up [nfsen](http://nfsen.sf.net)

Requirements
------------

No external dependencies.

Role Variables
--------------

The *nfsen* role has the following variables that can be overridden by
inventory:

- **nfsen_version**:  The package name and version string,
    eg. *nfsen-1.3.6p1*.
- **nfsen_url**:  The URL of the nfsen package.
- **netmon**: A dictionary to be used among several roles that describes
    monitored devices.

The netmon dictionary should look something like (in YAML):

    netmon:
        devices:
            - name: my_switch.example.net
              netflow:
                  port: 9995
                  col: #ff00ff
                  type: netflow

The parameters to the netflow dictionary are:

- **port**: The port nfcapd listens on for netflow data.  Set to *0* if
    you do not want a collector started.
- **col**: The color used in nfsen graphs
- **type**: Can be either *netflow* or *sflow*.


Dependencies
------------

Depends on [sfromm.epel](https://galaxy.ansible.com/list#/roles/1948).

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm.
