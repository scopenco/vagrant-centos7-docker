# CentOS 7 Vagrant environment with Docker

### Desciprion

This CentOS 7 [Vagrant](https://www.vagrantup.com/)  environment with Docker CE and AWS cli.
To access to host machine files may be used `/opt/Home` or `/opt/src` inside VM.

### Requirements

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [Fusion](https://www.vmware.com/go/downloadfusion) or [Parallels Desktop for Mac Pro Edition](http://www.parallels.com/products/desktop/download/)
* [Vagrant](https://www.vagrantup.com/downloads.html)

### Usage
1. Provision local VM with Vagrant
```bash
git clone git@github.mb-internal.com:ops/vagrant-centos7-docker.git
cd vagrant-centos7-docker
vagrant up
vagrant ssh
```

## Authors
* Author:: Andrei Skopenko (askopenko@malwarebytes.com)
