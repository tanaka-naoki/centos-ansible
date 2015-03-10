
Vagrant.configure(2) do |config|

  config.vm.box = "centos65"
  # config.vm.box_check_update = false
  
  config.vm.network "forwarded_port", guest:80, host:8880, id:"http"
  config.vm.network "private_network", ip: "192.168.33.10"

  # hostsの書き換えを行ってくれるplugin
  # vagrant plugin install vagrant-hostsupdater
   config.vm.hostname = "local.info"

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.gui = false
  
     # Customize the amount of memory on the VM:
     vb.memory = "1024"
   end

  # vagrant plugin install landrush
  #if defined?(Landrush)
  #  config.landrush.enabled = true
  #  config.vm.hostname = 'local'
  #  config.landrush.tld = 'local'
  #  config.landrush.guest_redirect_dns = false
  #end

  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end
