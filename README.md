maxhoesel.smb_mount
=========

A role to configure a systemd mount unit for a SMB share

Requirements
------------

- `become` privileges
- A host running Ubuntu or another Debian-based Linux distro

Role Variables
--------------

##### `smb_mount_src`
- URL of the SMB share to mount. Needs to be in the format understood by `mount`, such as `//server.com/mount_path`
- Required: yes

##### `smb_mount_dest`
- Path under which the share will be mounted. Must be absolute
- Must NOT have a dash in the file path - see the [systemd mount docs](https://www.freedesktop.org/software/systemd/man/systemd.mount.html) for details
- Required: yes

##### `smb_mount_guest`
- Whether to mount the share in guest mode
- Default: `no`

##### `smb_mount_username`
- Username with which to authenticate against the remote server. Required if `smb_mount_guest` is set to `no`

##### `smb_mount_password`
- Password with which to login on the remote server. Required if `smb_mount_guest` is set to `no`

##### `smb_mount_uid`
- Map the mount file owner to this local uid.
- fstab mount option equivalent: `uid=`
- Default: `{{ ansible_user_uid }}`

##### `smb_mount_gid`
- Map the mount file owner to this local gid.
- fstab mount option equivalent: `gid=`
- Default: `{{ ansible_user_gid }}`

##### `smb_mount_options`
- Additional mount options to pass to the mount unit
- Default: ""

License
-------

GPL 3 or later