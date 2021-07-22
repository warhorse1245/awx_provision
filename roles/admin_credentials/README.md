root_credentials
================

Sets root credentials

Requirements
------------

None

Role Variables
--------------

This role takes a single string value containing an encrypted password:

root_password: "encryptedpasswordvalue"

The encrypted password can be generated with standard python libraries:

$ python -c 'import crypt,getpass; print crypt.crypt(getpass.getpass())'



Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Set root credentials with task embedded variables
    - hosts: servers
      roles:
         - role: root_credentials
           vars:
             root_password: "{{ encryptedpasswordvalue }}"

License
-------

BSD

Author Information
------------------

EIS Linux
