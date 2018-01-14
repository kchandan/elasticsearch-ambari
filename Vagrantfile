# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  
  config.vm.box = "geerlingguy/centos7"

  
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "public_network"
  config.vm.synced_folder ".", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
   end
 
  config.vm.provision "shell", inline: <<-SHELL
     sudo curl http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.6.0.0/ambari.repo -o /etc/yum.repos.d/ambari.repo
     sudo yum install -y ambari-server ambari-agent git
     sudo ambari-server setup -s
     sudo git clone https://github.com/kchandan/elasticsearch-ambari.git /var/lib/ambari-server/resources/stacks/HDP/2.6/services/ELASTICSEARCH
     sudo ambari-server start
     sudo ambari-agent start
   SHELL
end
