# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.
  config.vm.box = "ubuntu/focal64"
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  #INSTALL PLUGINS
  config.vagrant.plugins = "vagrant-disksize" 
  config.vagrant.plugins = "vagrant-docker-compose"
  
  #Configs the "plugins"
  config.disksize.size = '40GB'
  config.vm.provision :docker
  config.vm.provision :docker_compose
  
  # Install vagrant-disksize to allow resizing the vagrant box disk.
  #unless Vagrant.has_plugin?("vagrant-disksize")
  #  raise  Vagrant::Errors::VagrantError.new, "vagrant-disksize plugin is missing. Please install it using 'vagrant plugin install vagrant-disksize' and rerun 'vagrant up'"
  #end
  

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # VirtualBox as a provider:
  config.vm.provider "virtualbox" do |vb|
  ## Display the VirtualBox GUI when booting the machine
    vb.gui = true
  ## Customize the amount of memory on the VM:
   	vb.memory = "2048"
  ## Customize the amount of CPUs on the VM:
    vb.cpus = 1
  ## Customize the amount of vRAM for GUI on the VM: ["modifyvm", :id, "--vram", "<vramsize in MB>"]
    #vb.customize ["modifyvm", :id, "–-vram", "12"] 
	
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
   sudo apt-get update
   sudo apt-get upgrade -y
   sudo loadkeys pt #To load pt keyboard
   sudo sed -i 's/XKBLAYOUT=\"us\"/XKBLAYOUT=\"pt\"/g' /etc/default/keyboard #change keyboard permanently
   sudo apt-get install neofetch #just to show information on terminal
   #sudo apt-get install -y xfce4 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
   sudo apt-get install -y gnome-session gnome-terminal virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11 #gnome vanilla
   sudo apt-get clean
   sudo apt-get autoremove
   sudo shutdown -r now
   #apt-get install -y apache2
  SHELL
end

