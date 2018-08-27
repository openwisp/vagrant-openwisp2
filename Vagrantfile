# -*- mode: ruby -*-
# vi: set ft=ruby :

if ARGV.length == 2
  if ARGV[1] == '-f'
    puts "You must use 'vagrant #{ARGV[0]} <name>, [<name>] ...'."
    puts "Run 'vagrant status' to view VM names."
    exit 1
  end
end

require 'yaml'
config_yml = YAML.load_file(File.join(__dir__, 'vagrant-config.yml'))

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Load plugins
  if Vagrant.has_plugin?('landrush')
    config.landrush.enabled = true
    config.landrush.host 'openwisp2.vagrant.test'
  else
    abort('Please install the landrush plugin, vagrant plugin install landrush')
  end

  config_yml[:vms].each do |name, settings|
    config.vm.define name do |vm_config|
      vm_config.vm.box = settings[:vbox]
      vm_config.vm.hostname = settings[:hostname]
      vm_config.vm.network 'private_network', ip: settings[:ip]
      vm_config.vm.synced_folder './', '/vagrant'
      vm_config.ssh.insert_key = false

      vm_config.vm.provider 'virtualbox' do |vb|
        vb.name = settings[:hostname]
        vb.cpus = settings[:cpu]
        vb.memory = settings[:memory]
      end

    
      # Ansible provisioner.
      vm_config.vm.provision :ansible do |ansible|
        ansible.playbook = 'provision/site.yml'
        ansible.inventory_path = 'provision/inventory'
        ansible.become = true
        ansible.host_key_checking = false
      end
    end
    # config.vm.provision "ansible" do |ansible|
    #   ansible.playbook = "provisioning/playbook.yml"
    #   ansible.inventory_path = "provisioning/inventory"
    #   ansible.become = true
    # end
  end
end
