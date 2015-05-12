Vagrant.configure(2) do |config|
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "chef/fedora-20"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", '4096']
    vb.customize ["modifyvm", :id, "--cpus", '2']
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # Enabling the Berkshelf plugin
  config.berkshelf.enabled = true

  # Lock Chef version to 12.3.0 to prevent future issues?
  config.omnibus.chef_version = '12.3.0'

  config.vm.provision :chef_solo do |chef|

    chef.json = {
      "elasticsearch" => {
        "version" => "1.5.2" # latest elastic search version, cookbook specifies "0.90.12"
      },
      "java" => {
        "install_flavor" => "openjdk",
        "jdk_version" => 7
      },
      "nodejs" => { # required to compile main.css
        "npm_packages" => [
          { "name" => "less" },
          { "name" => "gulp" }
        ]
      }
    }

    chef.add_recipe 'nodejs'
    chef.add_recipe 'atom::install_mysql'
    chef.add_recipe 'java'
    chef.add_recipe 'elasticsearch'
    chef.add_recipe 'apache2'
    chef.add_recipe 'php'
    chef.add_recipe 'php::module_mysql'
    chef.add_recipe 'apache2::mod_php5'
    chef.add_recipe 'atom'
  end
end
