
Vagrant.configure(2) do |config|

  config.vm.box = "centos65"
  # config.vm.box_check_update = false

  config.vm.network "forwarded_port", guest:80, host:8880, id:"http"
  config.vm.network "private_network", ip: "192.168.33.10"

  # hostsの書き換えを行ってくれるplugin
  # vagrant plugin install vagrant-hostsupdater
   config.vm.hostname = "local.info"
   config.hostsupdater.aliases = ["test.local.info"]

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.gui = false

     # Customize the amount of memory on the VM:
     vb.memory = "1024"

     vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
   end

  # vagrant plugin install landrush
  #if defined?(Landrush)
  #  config.landrush.enabled = true
  #  config.vm.hostname = 'local.info'
  #  config.landrush.tld = 'local.info'
  #  config.landrush.guest_redirect_dns = false
  #end

# ansibleをインストール
   config.vm.provision "shell", inline: <<-SHELL
     yum install -y ansible
     cd /vagrant/ansible
     ansible-playbook playbook.yml --connection=local
     SHELL
end
