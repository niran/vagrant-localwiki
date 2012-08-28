Vagrant::Config.run do |config|
  config.vm.define :appserver do |vm_config|
    vm_config.vm.box = "precise64"
    vm_config.vm.share_folder "localwiki", "/srv/localwiki", "../localwiki"
    vm_config.vm.share_folder "localwiki_data", "/usr/share/localwiki", "../localwiki_data"
    vm_config.vm.forward_port 8000, 8000
    vm_config.vm.provision :chef_solo do |chef|
      chef.log_level = :debug
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe("apt")
      chef.add_recipe("localwiki")
      chef.add_recipe("localwiki::develop")
      chef.add_recipe("localwiki::init_data")
      chef.add_recipe("localwiki::database")
    end
  end

  config.vm.define :postgis do |vm_config|
    vm_config.vm.box = "precise64"
    vm_config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe("apt")
      chef.add_recipe("localwiki")
    end
  end
end
