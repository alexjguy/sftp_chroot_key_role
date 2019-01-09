SFTP Chroot Public Key
=========

Ansible role that configures ubuntu for SFTP with users, chrooted directories and public key auth. This roles denies the from the defind group other type of login except sftp.

Requirements
------------

This role can be run on Ubuntu Server. It was tested on Ubuntu 18.06.

Role Variables
--------------

There are several variables that should be set and overriden for this role.

* chroot_home_directory - This will create a directory in / in which the jailed user directories will be into. Ex: /sftp/user1, /sftp/user2 .
* sftp_group_name - The OS group that allows users to login through sftp.
* users - a dictionary that contains an array of key value pairs.
..* name - the name of the user
..* ssh-public-key - the public key that will be added un authorised_keys
..* home_directory - the home directory of the user
..* ch_dirs - the directories created and in which the user can write into after he logs into ssh. These will be for example in the path: /sftp/user1/dir1, /sftp/user1/dir2, etc.
 
```
---
chroot_home_directory: sftp 
sftp_group_name: sftpusers
users:
  - name: user1 
    ssh-public-key: 'ssh-rsa-key'
    home_directory: /home/user1
    ch_dirs:
      - dir1 
      - dir2 
      - dir3
  - name: user2
    ssh-public-key: 'ssh-rsa-key'
    home_directory: /home/user2
    ch_dirs:
      - dir1 
      - dir2 
      - dir3
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: sftp
      roles:
         - { role: alexjgui.sftp_ch_pk, tags: sftp }

License
-------

None
