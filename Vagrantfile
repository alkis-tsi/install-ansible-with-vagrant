## Creating multiple nodes using Vagrant

## Script to install necessary packages and ansible for Centos test box.
## Comment out anything you do not want to install
$update_ansible_centos = <<-SCRIPT
cat << EOF
--------- Installing Updates ---------
    ()
   () ____
 _||__|  |  ______   ______   ______
(        | |      | |      | |      |
/-()---() ~ ()--() ~ ()--() ~ ()--()
--------------------------------------
EOF
yum update
yum install epel-release -y
yum install git -y
yum install vim -y
yum install ansible -y
SCRIPT

## Script to install necessary packages and ansible for Ubuntu test box.
## Comment out anything you do not want to install
$update_ansible_ubuntu = <<-SCRIPT
cat << EOF
--------- Installing Updates ---------
    ()
   () ____
 _||__|  |  ______   ______   ______
(        | |      | |      | |      |
/-()---() ~ ()--() ~ ()--() ~ ()--()
--------------------------------------
EOF
apt-get -y install software-properties-common
apt-add-repository -y ppa:ansible/ansible
apt-get -y update
apt-get -y install ansible
SCRIPT

Vagrant.configure("2") do |config|
## Configuration for spinning up a Centos box and installing ansible to it
  config.vm.define "test-centos" do |node|
    node.vm.box = "bento/centos-7.3"
    node.vm.network "public_network", ip: "192.168.87.100"
    node.ssh.insert_key = false
    node.vm.provider "virtualbox" do |vm|
      vm.customize ["modifyvm", :id, "--memory", 1024]
      vm.customize ["modifyvm", :id, "--cpus", 1]
      vm.customize ["modifyvm", :id, "--vram", "256"]
    end
    node.vm.provision "shell", inline: $update_ansible_centos
    node.vm.provision :file, source: '~/.vagrant.d/insecure_private_key', destination: '/home/vagrant/.ssh/id_rsa'
  end
## Configuration for spinning up an Ubuntu box and installing ansible to it
  config.vm.define "test-ubuntu" do |node|
    node.vm.box = "minimal/xenial64"
    node.vm.network "public_network", ip: "192.168.87.110"
    node.ssh.insert_key = false
    node.vm.provider "virtualbox" do |vm|
    vm.customize ["modifyvm", :id, "--memory", 1024]
    vm.customize ["modifyvm", :id, "--cpus", 1]
    vm.customize ["modifyvm", :id, "--vram", "256"]
    end
    node.vm.provision "shell", inline: $update_ansible_ubuntu
    node.vm.provision :file, source: '~/.vagrant.d/insecure_private_key', destination: '/home/vagrant/.ssh/id_rsa'
  end
end
