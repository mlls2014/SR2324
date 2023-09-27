# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

   config.vm.box = "bento/ubuntu-22.04" 
 
   config.vm.define "UBUDB" do |node|
     node.vm.hostname = "UBUDB"
     node.vm.network "private_network", ip: "192.168.200.254"
   end
    
   config.vm.synced_folder "./data", "/vagrant_data", create: true
  
   config.vm.provision "shell" do |s|
     s.inline = <<-SHELL
        apt update
        apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
        echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
           $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        apt update
        apt install docker-ce docker-ce-cli containerd.io -y
        apt install docker-compose -y
     SHELL
  end
 
 end
 