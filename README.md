ansible-role-nfsserver
======================
[![Build Status](https://travis-ci.org/uZer/ansible-role-nfsserver.svg?branch=master)](https://travis-ci.org/uZer/ansible-role-nfsserver)

* This role configures exports in /etc/exports. Will replace completely the file.

* All variables should be configured in `host_vars` or `group_vars`.

Dependencies
------------
Barely tested on Redhat 6, 7 and Ubuntu 14.04

Usage examples
--------------

```yaml
## NFSv3
nfs_exports:
  - dir: /srv/nfs_export1
    user: ypiolet
    group: ypiolet
    mode: '0770'
    clients:
      "test-vm-01.domain":
        - rw
        - sync
        - no_subtree_check

      "test-vm-02.domain":
        - ro
        - sync
        - no_subtree_check

## NFSv4
nfs_exports:
  - dir: /srv/nfs_export2
    clients:
      "gss/krb5i":
        - rw
        - sync
        - fsid=0
        - crossmnt
        - no_subtree_check

  - dir: /srv/nfs_export2/homes
    clients:
      "gss/krb5i":
        - rw
        - sync
        - no_subtree_check
```


License
-------
"THE (extended) BEER-WARE LICENSE" (Revision 42.0815):

As long as you retain this notice you can do whatever you want with this stuff.
If we meet some day, and you think this stuff is worth it, you can buy me some
beers in return.


Author Information
------------------
Youenn Piolet
