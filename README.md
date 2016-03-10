AtoM Vagrant
=============
This will create a Vagrant environment with [AtoM](https://www.accesstomemory.org/) installed on a CentOS 7.2 box.

This Vagrant configuration uses Chef to provision the VM using [atom_cookbook](https://github.com/ryersonlibrary/atom_cookbook) and [lits_vm](https://github.com/ryersonlibrary/lits_vm).

Requirements
------------
* [ChefDK](https://downloads.chef.io/chef-dk/)
* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](https://vagrantup.com)
* vagrant-berkshelf plugin `vagrant install plugin vagrant-berkshelf`
* vagrant-omnibus plugin `vagrant install plugin vagrant-omnibus`
* vagrant-hostsupdater plugin `vagrant install plugin vagrant-hostsupdater`

## Platform
This Vagrant configuration *should* work on:
* Ubuntu 14.04
* Windows 7 / 8 / 8.1 / 10

## Usage
1. `git clone --recursive https://github.com/ryersonlibrary/atom_vagrant`
2. `cd atom_vagrant`
3. `vagrant up`
4. Visit http://atom.dev on your browser

If you did not change the configuration, this is how you should fill in the fields on the web installer
* Database name: `atom`
* Database username: `atom`
* Database password: `atom`
* Database host: `localhost`
* Database port: `3306`
* Search host: `localhost`
* Search port: `9200`
* Search index: `atom`

## Known Issues
On some Windows hosts the `vagrant-hostsupdater` plugin will not work and you will have to edit your hosts file manually. 
* Your hosts file *should* be located at `C:\Windows\System32\drivers\etc`.
* Add this at the bottom your hosts file `192.168.33.10 atom.dev`

## Authors
* Patrick Fung (<patrick@makestuffdostuff.com>)
* MJ Suhonos (<mjsuhonos@ryerson.ca>)
