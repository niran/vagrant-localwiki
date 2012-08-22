Vagrant::Config.run do |config|
  config.vm.define :appserver do |vm_config|
    vm_config.vm.box = "precise64"
    vm_config.vm.share_folder "localwiki", "/srv/localwiki", "../localwiki"
    vm_config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe("apt")
      chef.add_recipe("localwiki")
      chef.add_recipe("localwiki::develop")
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
