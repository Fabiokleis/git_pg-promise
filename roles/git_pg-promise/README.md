Role Name
=========

Clona o repositorio [pg-promise](https://github.com/fabiokleis/pg-promise), instala dependencias, node modules, starta o codigo e postgresql localmente.

Requirements
------------

...

Role Variables
--------------
- `dir`: local do diretório do app
- `pg_conf`: local do arquivo de variáveis de ambiente do app

- [Variáveis](vars/main.yml)
- [Variáveis default](defaults/main.yml)
- Variáveis de ambiente do [pg-promise](templates/env.j2)

Dependencies
------------

...

Example Playbook
----------------
```yml
---
- hosts: pg_promise
  become: true
  roles:
    - role: git_pg_promise
```
License
-------

BSD

Author Information
------------------

...
