# -*- mode: ruby -*-
# vi: set ft=ruby :
# Author: askopenko@malwarebytes.com

load 'Vagrantfile.local' if File.exist?('Vagrantfile.local')

hostname = "centos7.dev"

$script = <<SCRIPT
# Base
yum -y install epel-release
yum -y update
yum -y install git vim-enhanced bash-completion
# Docker
yum -y install yum-utils device-mapper-persistent-data lvm2
test ! -f /etc/yum.repos.d/docker-ce.repo && yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum -y install docker-ce
yum -y install docker-compose
systemctl start docker
docker run hello-world
# AWS
yum -y install python-pip
pip install --upgrade pip
pip install --upgrade --user awscli
~/.local/bin/aws --version
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.hostname = hostname
  config.vm.box = "bento/centos-7.2"
  config.vm.provision "shell", inline: $script

  config.vm.provider "virtualbox" do |v, override|
    v.name = hostname
    v.memory = 1024
    v.cpus = 1
    v.linked_clone = true
    override.vm.synced_folder '~', '/opt/Home'
    override.vm.synced_folder './src', '/opt/src'
  end

  config.vm.provider "fusion" do |v, override|
    v.name = hostname
    v.memory = 1024
    v.cpus = 1
    v.linked_clone = true
    override.vm.synced_folder '~', '/opt/Home'
    override.vm.synced_folder './src', '/opt/src'
  end

  config.vm.provider "parallels" do |v, override|
    v.name = hostname
    v.memory = 1024
    v.cpus = 1
    v.linked_clone = true
    override.vm.synced_folder './src', '/opt/src', mount_options: ['share']
  end
end
