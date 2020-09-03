# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The Attacker's battle station.
  config.vm.define "kali", primary: true do |subconfig|
  subconfig.vm.box = "kalilinux/rolling"
  subconfig.vm.hostname = "kali"
  subconfig.vm.network :private_network, ip: "10.0.0.10"

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./public/", "/public/"
  end

  # Targets
  BOX_IMAGE = "ncaro/php7-debian8-apache-nginx-mysql"
  NODE_COUNT = 1
  (1..NODE_COUNT).each do |i|
    config.vm.define "target#{i}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "target#{i}"
      subconfig.vm.network :private_network, ip: "10.0.0.#{i + 10}"
    end
  end

  # Install avahi on all machines
  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y avahi-daemon libnss-mdns
  SHELL

end
