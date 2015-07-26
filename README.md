ARK server tools
=========

Provides an [ARK Survival Evolved](http://playark.com/) dedicated server, based on [Fezvrasta's](http://www.mywebexpression.com/) fantastic [ark-server-tools](https://github.com/FezVrasta/ark-server-tools).

Requirements
------------

The ARK dedicated server requires an x86_64 architecture.

Role Variables
--------------

The arkservertools role provides the following default options. **arkservertools_user** and **arkservertools_user_homedir** inherit from the *steamcmd* role to match the target server configuration.

```
arkservertools_url: "https://github.com/FezVrasta/ark-server-tools/archive/master.tar.gz"
arkservertools_user: "{{ steamcmd_user }}"
arkservertools_user_homedir: "{{ steamcmd_user_homedir }}"

arkservertools_ark_RCONPort: 32330
arkservertools_ark_SessionName: ARK Server Tools
arkservertools_ark_Port: 7778
arkservertools_ark_QueryPort: 27016
# If your using passwords and a public DCVS **ensure** you use ansible-vault!
#arkservertools_ark_ServerPassword:
arkservertools_ark_ServerAdminPassword: keyboardcat
arkservertools_ark_MaxPlayers: 70
```

When defining multiple servers, override these values using host_vars or inventory vars.

```
# inventory/all
vivid-64 arkservertools_ark_SessionName=vivid-x64.ark.cycloptivity.net
centos-7-64 arkservertools_ark_SessionName=centos-7-x64.ark.cycloptivity.net
jessie-64 arkservertools_ark_SessionName=jessie-x64.ark.cycloptivity.net
trusty-64 arkservertools_ark_SessionName=trusty-x64.ark.cycloptivity.net
```

Dependencies
------------

* steamcmd

Example Playbook
----------------

```
---
- hosts: ark
  roles:
  - kahn.steamcmd
  - kahn.arkservertools

```

License
-------

MIT

Author Information
------------------

Sam Wilson - http://www.cycloptivity.net/
