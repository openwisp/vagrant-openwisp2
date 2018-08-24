# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/stretch64"

end


VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/stretch64"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "openwisp2"
    v.memory = 512
    v.cpus = 2
  end

  config.vm.hostname = "openwisp2"
  config.vm.network :private_network, ip: "192.168.56.2"

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.vm.define :openwisp2 do |openwisp2|
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.become = true
  end

end
