NOTES
=====

ansible 'files' directory
-------------------------

- We break the ansible role directory structure a little bit by throwing files and templates together in the same path: files/{{ app }}/
  This way we only have to open/expand one directory to see all files for a specific app

- use `un_install_env` to copy config files that are not part of the app's git repository. 
  Obviously they should not be part of this role's git repository either. But we have the options to encrypt these files later!


TO DO
=====

- Encrypt config files and secrets so that they may be part of the git repository

ATTENTION
=========

`un_install_state: absent` currently only removes
- the app directory
- the link created to the executable
--> It does not handle systemd units (remove/stop/disable)

LINKS
=====

- https://docs.ansible.com/ansible/latest/collections/ansible/builtin/git_module.html