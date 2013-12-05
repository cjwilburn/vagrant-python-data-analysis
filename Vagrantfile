# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :pythondata do |pythondata_config|
    # Every Vagrant virtual environment requires a box to build off of.
    pythondata_config.vm.box = "precise64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    pythondata_config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    # Forward a port from the guest to the host, which allows for outside
    # computers to access the VM, whereas host only networking does not.
    # pythondata_config.vm.forward_port 80, 8080
    # pythondata_config.vm.forward_port 8000, 8001
    # pythondata_config.vm.forward_port 9999, 9998

      # Use hostonly network with a static IP Address
  # and enable hostmanager
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.vm.define 'jasper' do |node|
    node.vm.hostname = 'jasper.local'
    node.vm.network :private_network, ip: '192.168.17.17'
    node.hostmanager.aliases = %w(www.jasper.local)
  end
  config.vm.provision :hostmanager

    pythondata_config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe "apt"
      chef.add_recipe "apache2::mod_wsgi"
      chef.add_recipe "build-essential"
      chef.add_recipe "git"
      chef.add_recipe "python"
      chef.json = {
        "python-data" => {
            "virtualenv_dir" => "/home/vagrant/env/",
            "virtualenv_name" => "pythondata"
        }, 
        "gurobi-installer" => {}
      }
      chef.add_recipe "python-data"
      chef.add_recipe "openssl"
    end
  end
end