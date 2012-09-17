Vagrant::Config.run do |config|
  config.vm.define :appserver do |vm_config|
    vm_config.vm.box = "precise64"
    vm_config.vm.share_folder "localwiki", "/srv/localwiki", "../localwiki"
    vm_config.vm.share_folder "localwiki_data", "/usr/share/localwiki", "../localwiki_data"
    vm_config.vm.forward_port 8000, 8000
    vm_config.vm.provision :chef_solo do |chef|
      chef.log_level = :debug
      chef.cookbooks_path = "cookbooks"
      chef.roles_path = "roles"
      chef.add_role("localwiki_monolithic_vagrant")

      # vagrant-ec2 support
      require 'json'
      open('ec2-dna.json', 'w') do |f|
        chef.json[:run_list] = ["role[localwiki_monolithic]"]
        f.write chef.json.to_json
      end
    end
  end
end
