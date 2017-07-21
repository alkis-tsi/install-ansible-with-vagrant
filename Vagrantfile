## Creating multiple nodes using Vagrant

## Scripts to install necessary packages and ansible for Centos test box.
## Comment out anything you do not want to install
$update_ansible_centos = <<-SCRIPT
cat << EOF
--------- Installing Updates ---------
____
_||__|  |  ______   ______   ______
(        | |      | |      | |      |
/-()---() ~ ()--() ~ ()--() ~ ()--()
EOF
yum update
yum install epel-release -y
yum install git
yum install vim
yum install ansible -y
SCRIPT


## Scripts to install necessary packages and ansible for Ubuntu test box.
## Comment out anything you do not want to install
$update_ansible_ubuntu = <<-SCRIPT
cat << EOF
--------- Installing Updates ---------
____
_||__|  |  ______   ______   ______
(        | |      | |      | |      |
/-()---() ~ ()--() ~ ()--() ~ ()--()
EOF
apt-get install software-properties-common
apt-add-repository ppa:ansible/ansible
apt-get update
apt-get install ansible
SCRIPT

Vagrant.configure("2") do |config|
## Configuration for spinning up a Centos box and installing ansible to it
  config.vm.define "test-centos" do |node|
    node.vm.box = "bento/centos-7.3"
    node.vm.network "public_network", ip: "192.168.87.100"
    node.ssh.username = "vagrant"
    node.ssh.password = "vagrant"
    node.ssh.insert_key = true
    node.ssh.pty = false
    node.vm.provider "virtualbox" do |vm|
      vm.gui = true
      vm.customize ["modifyvm", :id, "--memory", 1024]
      vm.customize ["modifyvm", :id, "--cpus", 1]
      vm.customize ["modifyvm", :id, "--vram", "256"]
    end
    node.vm.provision "shell", inline: $update_ansible_centos
  end
## Configuration for spinning up an Ubuntu box and installing ansible to it
  config.vm.define "test-ubuntu" do |node|
    node.vm.box = "boxutter/ubutnu"
    node.vm.network "public_network", ip: "192.168.87.110"
    node.ssh.username = "vagrant"
    node.ssh.password = "vagrant"
    node.ssh.insert_key = true
    node.ssh.pty = false
    node.vm.provider "virtualbox" do |vm|
    vm.gui = true
    vm.customize ["modifyvm", :id, "--memory", 1024]
    vm.customize ["modifyvm", :id, "--cpus", 1]
    vm.customize ["modifyvm", :id, "--vram", "256"]
    end
    node.vm.provision "shell", inline: $update_ansible_ubuntu
  end
end
