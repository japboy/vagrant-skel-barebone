vagrant-skel-barebone
=====================

My initial Vagrant skeleton provisioning with Ansible.

Requirements
------------

* [Vagrant](http://www.vagrantup.com/)
    * [dotenv](https://github.com/bkeepers/dotenv)
* [Ansible](http://www.ansible.com/)

As virtualizing providers;

* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant AWS Provider](https://github.com/mitchellh/vagrant-aws)
* [Vagrant GCE Provider](https://github.com/mitchellh/vagrant-google)
* [Vagrant DigitalOcean Provider](https://github.com/smdahlen/vagrant-digitalocean)
* [Vagrant ManagedServers Provider](https://github.com/tknerr/vagrant-managed-servers)

A Box file used for VirtualBox;

* [japboy/CentOS-7.0-1406-x86_64-Minimal](https://vagrantcloud.com/japboy/CentOS-7.0-1406-x86_64-Minimal)

Installation
------------

Install `dotenv` plugin into your Vagrant environment first:

```
vagrant plugin install dotenv
```

If you use additional Vagrant providers, install them as well:

```
vagrant plugin install vagrant-aws vagrant-google vagrant-digitalocean vagrant-managed-servers
```

If you use with VirtualBox, install the Box file first:

```
vagrant box add japboy/CentOS-7.0-1406-x86_64-Minimal
```

Bootstrap
---------

First of all, copy this repository as your project bootstrap, then follow the instruction below.

Create your `.env` file to store your environment variables like host or user name, password, secret tokens, and so on. It will be used by `Vagrantfile` through `ENV['VARIABLE']` variables.

These are basic commands to work with Vagrant:

Start working on the project with VirtualBox:

```
cd /path/to/proj
vagrant up
```

With Amazon Web Services:

```
vagrant up --provider=aws
```

With Google Compute Engine:

```
vagrant up --provider=google
```

With DigitalOcean:

```
vagrant up --provider=digital_ocean
```

With a physical server:

```
vagrant up --provider=managed
```

Access the LAMP environment under `./public/www/html` through a web browser:

http://192.168.33.10/

References
----------

* [Ansible - Provisioning - Vagrant Documentation](http://docs.vagrantup.com/v2/provisioning/ansible.html)
* [Using Vagrant and Ansible — Ansible Documentation](http://docs.ansible.com/guide_vagrant.html)
* [Best Practices — Ansible Documentation](http://docs.ansible.com/playbooks_best_practices.html)
* [Insanely complete Ansible playbook, showing off all the options](https://gist.github.com/marktheunissen/2979474)

License
-------

Distributed under [Unlicense](http://unlicense.org/)
