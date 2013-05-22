# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = 'ruby_base'
  config.vm.box_url = 'https://www.dropbox.com/s/47tb2867l7jfwok/ruby_base.box'

  config.vm.network :private_network, ip: '10.10.10.10'
  config.vm.network :forwarded_port, guest: 3000, host: 3001

  config.vm.synced_folder '.', '/vagrant', nfs: true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.berkshelf.enabled = true

  # Provision with chef (solo)
  config.vm.provision :chef_solo do |chef|
    chef.add_recipe 'apt'
    chef.add_recipe 'build-essential'
    chef.add_recipe 'postgres_vagrant'
    chef.add_recipe 'rvm::vagrant'
    chef.add_recipe 'rvm::system'
    chef.add_recipe 'standard_packages'
    chef.add_recipe 'rails_development::postgres'

    chef.json = {
      'postgresql' => {
        'password' => { 'postgres' => 'xnvfzujhgcpitorlqewb' }
      },
      'rvm' => {
        'default_ruby' => '2.0.0@vagrant'
      }
    }
  end

end
