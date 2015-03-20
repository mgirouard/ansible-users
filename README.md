User Role for Ansible
=====================

A [somewhat] opinionated Ansible role for automating users.

This assumes that there will be two initial users: an ops user and a regular
(non-privileged) user. The primary difference between the two is that the ops
user will have unrestricted sudo access. These users have keypairs generated
automatically for them.

Each user has different `authorized_keys` that will be deployed allowing for
separate app and ops teams to use the box.

Configuration
-------------
* `app_user`: The non-privileged username.
* `ops_user`: The sudo-privileged username intented for operations.

To Do
-----
* Allow for additional users to be created
* Initialize a ~/bin directory
* Allow for finer-graned user settings (home dir, primary/secondary groups,
  etc)
