NOTES
=====

Ansible 'files' directory
-------------------------

- We break the ansible role directory structure a little bit by throwing files and templates together in the same path: files/{{ app }}/
  This way we only have to open/expand one directory to see all files for a specific app

- use `un_install_env_src` to copy config files that are not part of the app's git repository. 
  Obviously they should not be part of this role's git repository either. But we have the options to encrypt these files later!


EXAMPLE
=======

```yml
# fk.toolbox-user
- ansible.builtin.import_role:
	name: un-install
	tags: [un-install, fk.toolbox-user]
	vars:
	un_install_app: fk.toolbox-user
	un_install_user: udo
	un_install_with_git_url: ssh://git@192.168.10.100:2224/franzk-it/fk.toolbox-user.git
	un_install_with_git_force: true
	un_install_desktop: fk.toolbox-user.desktop.j2
	un_install_icon: src/icon.png
	un_install_polkit_rules:
	- fk.toolbox-user.rules
```


TO DO
=====

- [ ] Encrypt config files and secrets so that they may be part of the git repository
- [ ] `state: absent` should also handle removal of systemd


LINKS
=====

- https://docs.ansible.com/ansible/latest/collections/ansible/builtin/git_module.html