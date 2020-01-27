Ansible role: Plenv
=========

An Ansible Role that installs [Plenv](https://github.com/tokuhirom/plenv) with Perl on RedHat/CentOS or Debian/Ubuntu.

Requirements
------------

none.

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

`plenv_perl_flags: -j 9 -D usethreads -D man1dir=none -D man3dir=none` 

Flags that are used by `gcc` while configuring/compiling Perl from source.

`app_user_internal: "{{ app_user | default('vagrant') }}"`

The default user under which `plenv` annd `perl` will be installed. Defaults to: vagrant.

```
plenv:
  bin: "{{ home_path }}/.plenv/bin/plenv"
  url: https://github.com/tokuhirom/plenv.git
  user: "{{ app_user_internal }}"
  local: "{{ plenv_local | default('5.26.1') }}"
```

Set where `plenv` will be installed and which version of `perl` will be installed. Default version: 5.26.1
After installation, you can use `plenv` to install and switch to different versions of `perl`.

```
perl_build:
  url: https://github.com/tokuhirom/Perl-Build.git
  path: "{{ home_path }}/.plenv/plugins/perl-build"
```

Set where `perl_build` will be installed. Defaults: `.plenv` folder in the `$HOME` folder of the `app_user`.


Dependencies
------------

none.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: netsensei.plenv }

License
-------

MIT

Author Information
------------------

This role was created by [Matthias Vandermaesen](https://github.com/netsensei) in 2020.