#####################################################################################
# Vagrant Development Environment for FullStack JavaScript applications.            #
#                                                                                   #
# Author: Gabo Esquivel                                                             #
#-----------------------------------------------------------------------------------#
# Prerequisites: Virtualbox, Vagrant                                                #
# Usage: command 'vagrant up' in the folder of the Vagrantfile                      #
#####################################################################################

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# This Vagrant environment requires Vagrant 1.6.0 or higher.
Vagrant.require_version ">= 1.6.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Specify the base box
  config.vm.box = "ubuntu/trusty64"

  # ionic
  config.vm.network "forwarded_port", guest: 8100, host: 8100
  # livereload
  config.vm.network "forwarded_port", guest: 35729, host: 35729
  # backend app
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  config.vm.synced_folder "source/", "/var/project/source/"
  config.vm.synced_folder "resources/", "/var/project/resources/"

  config.vm.hostname = "jsbox"
  #config.vm.network :private_network, ip: "192.168.101.101"

  # Provision the VirtualBox with Ansible
  # Requires https://github.com/vovimayhem/vagrant-guest_ansible on windows

  if Vagrant::Util::Platform.windows?
    config.vm.provision :guest_ansible do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.raw_arguments = ['-v']
    end
  else
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.raw_arguments = ['-v']
    end
  end

  # Configure VM settings for server running in VirtualBox
  config.vm.provider "virtualbox" do |vb|
    # set the Video Ram to 128 megs
    vb.customize ["modifyvm", :id, "--vram", "128"]
    # turn on the USB drivers so that we can connect an Android device
    vb.customize ["modifyvm", :id, "--usb", "on"]
    # add a usb device filter for a Android Device
    vb.customize ["usbfilter", "add", "0", "--target", :id, "--name", "android", "--vendorid", "0x18d1"]
    # this is the name in the VirtualBox Manager UI
    vb.name = "JSBox"
    # set the system memory for the virtual machine
    vb.memory = 2048
    # number of Physical CPUs to allocate
    vb.cpus = 2
  end

end
