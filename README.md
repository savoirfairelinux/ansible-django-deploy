# ansible-django-deploy

*Provisions a Django project, SFL style.*

Running this roles results in the creation of a fully functional Django instance, isolated in a
Python virtualenv. The operations provided by this role (requirements installation, migrations execution, ...)
can be performed in non-privileged mode.

## Requirements

* Ansible 2.2+

## Usage

You call this role as with any other roles. See [vars file](defaults/main.yml) for customisation
options.

Here's an example usage for a local development environment:

```yaml
---
- name: Install a fully functional Django
  hosts: django-dev

  roles:
    - role: django-deploy
      django_user: vagrant
```
