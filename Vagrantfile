Vagrant.configure(2) do |config|
  
  config.vm.define "leaf1" do |leaf1|
    leaf1.vm.box = "cumulus-linux-3.3.1-vx-amd64-1495771745.c1063bczfc5ca01.box"
    # Internal network for swp* interfaces.
    leaf1.vm.network "private_network", virtualbox__intnet: "sp1swp1-lf1swp1", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "sp2swp1-lf1swp2", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp3-lf2swp3", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
  end
  
  config.vm.define "leaf2" do |leaf2|
    leaf2.vm.box = "cumulus-linux-3.3.1-vx-amd64-1495771745.c1063bczfc5ca01.box"
    # Internal network for swp* interfaces.
    leaf2.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf2swp1", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf2swp2", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp3-lf2swp3", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
  end

  config.vm.define "spine1" do |spine1|
    spine1.vm.box = "cumulus-linux-3.3.1-vx-amd64-1495771745.c1063bczfc5ca01.box"
    # Internal network for swp* interfaces.
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp1-lf1swp1", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf2swp1", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp3", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
  end

  config.vm.define "spine2" do |spine2|
    spine2.vm.box = "cumulus-linux-3.3.1-vx-amd64-1495771745.c1063bczfc5ca01.box"
    # Internal network for swp* interfaces.
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp1-lf1swp2", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf2swp2", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp3", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
  end
 
end
