Vagrant.configure(2) do |config|
  
  config.vm.define "leaf1" do |leaf1|
    leaf1.vm.box = "CumulusCommunity/cumulus-vx"
    # Internal network for swp* interfaces.
    leaf1.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "sp1swp1-lf1swp1", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "sp2swp1-lf1swp2", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp3-lf2swp3", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
    #set network interfaces to vbox promiscuous mode
    leaf1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    leaf1.vm.provision "shell", inline: <<-SHELL
      sudo net add interface swp1 ip address 10.0.0.1/24
      sudo net commit
    SHELL
  end
  
  config.vm.define "leaf2" do |leaf2|
    leaf2.vm.box = "CumulusCommunity/cumulus-vx"
    # Internal network for swp* interfaces.
    leaf2.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf2swp1", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf2swp2", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp3-lf2swp3", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
    #set network interfaces to vbox promiscuous mode
    leaf2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    leaf2.vm.provision "shell", inline: <<-SHELL
      sudo net add interface swp1 ip address 10.0.0.2/24
      sudo net commit
    SHELL
  end

  config.vm.define "spine1" do |spine1|
    spine1.vm.box = "CumulusCommunity/cumulus-vx"
    # Internal network for swp* interfaces.
    spine1.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp1-lf1swp1", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf2swp1", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp3", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
    #set network interfaces to vbox promiscuous mode
    spine1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    spine1.vm.provision "shell", inline: <<-SHELL
      sudo net add interface swp1 ip address 10.0.0.3/24
      sudo net commit
    SHELL
  end

  config.vm.define "spine2" do |spine2|
    spine2.vm.box = "CumulusCommunity/cumulus-vx"
    # Internal network for swp* interfaces.
    spine2.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp1-lf1swp2", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf2swp2", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp3", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
    #set network interfaces to vbox promiscuous mode
    spine2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    spine2.vm.provision "shell", inline: <<-SHELL
      sudo net add interface swp1 ip address 10.0.0.4/24
      sudo net commit
    SHELL
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "ubuntu/xenial64"
    ansible.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    ansible.vm.provision "shell", inline: <<-SHELL
     sudo ifconfig enp0s8 10.0.0.20/24
     sudo apt-get update
     sudo apt-get install git vim python-netaddr python-pip sshpass -y
     sudo pip install ansible
     git clone https://github.com/mattincarlsbad/ansible-cumulus-training-vagrant
    SHELL
  end

end
