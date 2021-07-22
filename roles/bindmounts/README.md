Role Name
=========

Creates bind mount for /tmp -> /var/tmp as a requirement for CIS.  This is done here because the Satellite cannot create bind mounts during kickstart.

Requirements
------------

None

Role Variables
--------------

None, values are hardcoded

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - bindmount

License
-------

BSD

Author Information
------------------

EIS Linux
