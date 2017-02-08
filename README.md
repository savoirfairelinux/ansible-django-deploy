# ansible-django-deploy

*Provisions a Django project, SFL style.*

Running this roles results in the creation of a fully functional Django instance, isolated in a
Python virtualenv. The operations provided by this role (requirements installation, migrations
execution, ...) can be performed in non-privileged mode.

## Requirements

* Ansible 2.2+
* Something to serve the deployed django app. See below.

### Serving the deployed django app

This role only takes care of deploying a django project's code and perform tasks generally
associated with this deployment (migrations, etc.). It **doesn't** configure a HTTP server to
expose that app.

Therefore, you need another role to provision this part. A good option would be
[ansible-django][ansible-django] which configures nginx and uwsgi to serve a django app, which fits
nicely with this role, because that's exactly what we provide!

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

[ansible-django]: https://github.com/savoirfairelinux/ansible-django
