# FullStack JavaScript Vagrant Box

A Vagrant Box for Hybrid and Node Apps Development

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

* Vagrant
* Virtualbox

If you are on window you are going need the guest_ansible plugin   
`vagrant plugin install vagrant-guest_ansible`


## Provisioning

The provisioning is a Ansible process on the local/guest side, so you dont have to worry about installing Ansible.



#### Shared folders

Your projects is shared in:
``/var/project/source``

All resources e.g. database dump:
``/var/project/resources/``

# Licence

MIT
