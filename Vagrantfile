Vagrant::Config.run do |config|
  config.vm.define :postgis do |pg_config|
    pg_config.vm.box = "precise64"
    pg_config.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "cookbooks"
      chef.add_recipe("apt")
      chef.add_recipe("geodjango")
    end
  end
end