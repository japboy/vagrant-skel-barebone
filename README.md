vagrant-skel-barebone
=====================

My initial Vagrant skeleton provisioning with Ansible.

* Based on [japboy/CentOS-7.0-1406-x86_64-Minimal](https://vagrantcloud.com/japboy/CentOS-7.0-1406-x86_64-Minimal) distributed under [Vagrant Cloud](https://vagrantcloud.com/)

Requirements
------------

* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](http://www.vagrantup.com/)
* [Ansible](http://www.ansible.com/)

Installation
------------

Install `dotenv` plugin into your Vagrant environment first:

```
vagrant plugin install dotenv
```

Bootstrap
---------

First of all, copy this repository as your project bootstrap.

Everytime when you are working on the project:

```
cd /path/to/proj
vagrant up
```

Then access the URL below:

[https://192.168.33.10/](https://192.168.33.10/)

References
----------

* [Ansible - Provisioning - Vagrant Documentation](http://docs.vagrantup.com/v2/provisioning/ansible.html)
* [Using Vagrant and Ansible — Ansible Documentation](http://docs.ansible.com/guide_vagrant.html)
* [Best Practices — Ansible Documentation](http://docs.ansible.com/playbooks_best_practices.html)
* [Insanely complete Ansible playbook, showing off all the options](https://gist.github.com/marktheunissen/2979474)

License
-------

Distributed under [Unlicense](http://unlicense.org/)
