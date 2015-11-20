# FullStack JavaScript Vagrant Box

A Vagrant Box for Hybrid and Node Apps Development

__NOTE:  this is a work in progress. Contributions are welcome.__

## Includes

* Git
* MongoBD
* Node Version Manager ( nvm )
* Automatic NodeJS Version Switching ( avn )
* Hybrid App Dev Ready
  * Android SDK
  * java-7-openjdk
  * cordova
  * ionic

## Requirements

* [Vagrant](https://www.vagrantup.com/)
* [Virtualbox](https://www.virtualbox.org/)

If you are on window you are going need the guest_ansible plugin   
`vagrant plugin install vagrant-guest_ansible`

## Installation

```
git clone git@github.com:gaboesquivel/jsdevbox.git
cd jsdevbox
vagrant up
```

## Provisioning

The provisioning is a Ansible process on the local/guest side, so you don't have to worry about installing Ansible.

NOTE: Vagrant will provision the virtual machine only once on the first run, any subsequent provisioning must be executed with the ``--provision` flag either `vagrant up --provision` or `vagrant reload --provision` or `vagrant provision` if vagrant box is already running. The provisioning will re-run also if you destroy the VM and rebuild it with vagrant destroy and vagrant up.  

## Shared folders

Your projects is shared in:
``/var/project/source``

All resources e.g. database dump:
``/var/project/resources/``

## Vagrant
There’s a ton of commands you can use to talk to Vagrant. For a full list see the [official docs](http://docs.vagrantup.com/v2/cli/), but here are the more common ones.

* `vagrant up` - use this command to `start` your virtual environment
* `vagrant halt` - use this command to `stop` your virtual environment
* `vagrant suspend` - use this command to `pause` your virtual environment, make sure you do this before shutting down your computer to safely be able to restore the environment later.
* `vagrant destroy` - use this command to `removes` your virtual environment from your machine
* `vagrant reload` - use this command to your virtual environment, if you add the `--provision` flag, it will reprovision the box as well; this is useful with removing or adding things to the server via Ansible.
* `vagrant ssh` - use this command to `connect` to the virtual server

# Licence

MIT
