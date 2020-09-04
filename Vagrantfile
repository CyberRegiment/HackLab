# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
config.vm.synced_folder ".", "/vagrant", disabled: true

  # The Attacker's battle station.
  config.vm.define "kali", primary: true do |subconfig|
  subconfig.vm.box = "kalilinux/rolling"
  subconfig.vm.network :private_network, ip: "10.0.0.10"
  subconfig.vm.synced_folder "./public/", "/public/"
  subconfig.vm.provider "virtualbox" do |v|
    v.gui = true
    v.name = "kali"
    v.memory = 4096
    v.cpus = 2
    end
  end

  # Targets
  BOX_IMAGE = "miya0001/vccw"
  NODE_COUNT = 1
  (1..NODE_COUNT).each do |i|
    config.vm.define "target#{i}", autostart: false do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "target#{i}"
      subconfig.vm.network :private_network, ip: "10.0.0.#{i + 10}"
    end
  end

  # Execute automated deployment scripts
  config.vm.provision "ansible", after: :all do |ansible|
    ansible.compatibility_mode = "auto"
    ansible.verbose = "v"

    # Call the default playbook.
    ansible.playbook = "provisioning/site.yml"

    # Optionally filter tags (string or array of strings)
    ansible.tags = ["all"]

    # Set of inventory groups to be included in the auto-generated inventory file.
    ansible.groups = {
      "attackers" => ["kali"],
      "kali:vars" => {"ansible_sudo_pass" => "vagrant"}
    }

    # Limit target boxes to a subset.
    # ansible.limit = ""

    ansible.ask_become_pass = false

    # default password for vagrant boxes to allow sudo priviledges
    ansible.extra_vars = {
      ansible_sudo_pass: "vagrant"
    }
  end

end
