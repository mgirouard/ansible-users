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
This role expects there to be a `users` array defined which can have any of the
following keys defined:

* `username`: The name of the user.
* `keys_generate`: Whether or not to generate keys
* `keys_bits`: Number of bits to include in SSH key
* `is_admin`: Whether or not the user will have passwordless sudo privs

The only required key is the `username` key. 

### Example

    users: [
      { username: 'foo' },
      { username: 'bar', keys_generate: true },
      { username: 'baz', keys_generate: true, keys_bits: 4086 },
      { username: 'bif', keys_authorized: "~/.ssh/id_rsa.pub" },
      { username: 'thud', is_admin: true }
    ]

To Do
-----
* Initialize a ~/bin directory
* Allow for finer-graned user settings (home dir, primary/secondary groups,
  etc)
