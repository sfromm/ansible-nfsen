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
  monitored devices.  Described below.
- **nfsen_php_timezone**:  The default timezone for PHP.  Defaults to
  *UTC*.
- **nfsen_mail_from**:  Email address used by **nfsen** when sending
  email.  Defaults to *nobody@localhost*.
- **nfsen_smtp_server**:  SMTP server to use when sending email.
  Defaults to *localhost*.
- **nfsen_syslog_facility**:  Syslog facility used by **nfsen** for
  logging.  Defaults to *daemon*.
- **nfsen_colors**:  A list of hexadecimal colors to use for profiles.
  This is used if you do not define a color per netflow source.

The following variables control what paths are used by **nfsen**.

- **nfsen_bindir**:  Directory where binaries are located.  Defaults to
  */usr/local/bin*.
- **nfsen_libexecdir**: Directory where internal binaries are located.
  Defaults to */usr/local/libexec/nfsen*.
- **nfsen_confdir**: Directory where configuration file is stored.
  Defaults to */etc*.
- **nfsen_vardir**:  Directory where state files are stored.  Defaults
  to */var/lib/nfsen*.
- **nfsen_piddir**:  Directory where PID file and socket exist.
  Defaults to */var/run/nfsen*.
- **nfsen_htmldir**:  Directory path of HTML and PHP files.  Defaults to
  */var/www/nfsen*.


The *netmon* dictionary should look something like (in YAML):

    netmon:
        devices:
            - name: my_switch.example.net
              ext:
                nfsen:
                  port: 9995
                  col: #ff00ff
                  type: netflow

The parameters to the netflow dictionary are:

- **port**: The port nfcapd listens on for netflow data.  Set to *0* if
    you do not want a collector started.
- **col**: The color used in nfsen graphs
- **type**: Can be either *netflow* or *sflow*.

For more information regarding *netmon*, please see: [netmon.org](netmon.org).

Dependencies
------------

Depends on [sfromm.epel](https://galaxy.ansible.com/list#/roles/1948).

Example Playbook
----------------

A simple example:

    - hosts: servers
      roles:
         - { role: sfromm.nfsen }

License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm.
