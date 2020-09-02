# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # Define boxes
  config.vm.define "kali", primary: true do |subconfig|
  subconfig.vm.box = "kalilinux/rolling"
  subconfig.vm.hostname = "kali"
  subconfig.vm.network :private_network, ip: "10.0.0.10"
  end

  config.vm.define "target1", autostart: false do |subconfig|
  subconfig.vm.box = "ncaro/php7-debian8-apache-nginx-mysql"
  subconfig.vm.hostname = "target1"
  subconfig.vm.network :private_network, ip: "10.0.0.11"
  end

  # Install avahi on all machines
  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y avahi-daemon libnss-mdns
  SHELL

end
