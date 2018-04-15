Ansible Role: GitLab Community Edition
=========

_**WARNING**_: due to GitLab CE system requirements, the playbook might fail if the target host does not 
have enough RAM.

This role installs and configure GitLab Community Edition. Note that this particular role can be used with the following (it is optional though):
- [ansible-role-webserver](https://github.com/GSquad934/ansible-role-webserver)


Without Nginx installed, this role performs the following actions:
- Setup a repository for GitLab
- Install the latest version of GitLab Community Edition
- Configure GitLab Community Edition with the default options


In this configuration, GitLab can be accessed via *http://<server_ip>*

---


If Nginx is installed (using the role above), this role performs the following actions:
- Setup a repository for GitLab
- Install the latest version of GitLab Community Edition
- Configure GitLab Community Edition so it listens only on 127.0.0.1 on a chosen port (8082 by default)
- Create and enables a site in Nginx to access GitLab on a specific hostname (HTTPS is enforced either via Let's Encrypt, or using some generic certificates)


When Nginx is installed, you can configure a specific hostname to access GitLab (see the variables below).


Role Variables
--------------

If GitLab is used without Nginx, then no variables are actually required.

When using Nginx, multiple variables can be configured.

Here is how they can be configured:

```
gitlab_hostname: gitlab.mysite.com
gitlab_port: 8082 *(this must be an unused port on your system)*
certbot_email: mymail@mail.com *(email address used for validation by Let's Encrypt)*
```

The variables above can be configured as host_vars for example.

Dependencies
------------

*(Optional)* This role can depend on the following one if you wish to use Nginx as a Web server:
- [ansible-role-webserver](https://github.com/GSquad934/ansible-role-webserver)


If you install this role via Ansible-Galaxy, the name of the rolee is [*GSquad934.webserver*](https://github.com/GSquad934/ansible-role-webserver).


However, if you already have Nginx installed, this role should still work.

Example Playbook
----------------

Here is a simple example playbook to use this role:

```
hosts: gitlab-ce_srv
user: myuser
become: true
roles:
  - { role: gitlab-ce, tags: [ 'gitlab-ce' ] }
```

License
-------

MIT / BSD

Author Information
------------------

My name is Gaétan. You can follow me on [Twitter](https://twitter.com/gaetanict)

Website: [ICT Pour Tous](https://www.ictpourtous.com)
