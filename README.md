### This is a simple installation of Ansible with Vagrant using VirtualBox


#### Requirements
- Virtual Box (latest version)
- Vagrant (latest version)

#### Instructions - Usage
At you command line simply clone this repository and then run:
```
$ vagrant status            ## it will show you which boxes are running
$ vagrant up test-centos    ## it will only spin up 1 Centos box
$ vagrant ssh test-centos   ## it will give you ssh access to that box
```
or
```
$ vagrant status            ## it will show you which boxes are running
$ vagrant up test-ubuntu    ## it will only spin up 1 Ubuntu box
$ vagrant ssh test-ubuntu   ## it will give you ssh access to that box
```
