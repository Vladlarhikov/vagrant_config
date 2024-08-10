# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
    config.vm.define "s01kuber" do |controlnode|
      controlnode.vm.box = "ubuntu/focal64"
      controlnode.vm.hostname = "s01kuber"
      controlnode.vm.network "private_network", ip: "192.168.50.6"
      controlnode.vm.synced_folder "./ansible","/home/vagrant/ansible"
      controlnode.vm.provision "shell", inline: <<-SHELL
        sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
        service ssh restart
      SHELL
    end
    # Every Vagrant development environment requires a box. You can search for
    # boxes at https://vagrantcloud.com/search.
    config.vm.define "s02kuber" do |server|
     server.vm.box = "ubuntu/focal64"
     server.vm.hostname = "s02kuber"
     server.vm.network "private_network", ip: "192.168.50.7"
     server.vm.provision "shell", inline: <<-SHELL
       sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
       service ssh restart
     SHELL
    end
   end