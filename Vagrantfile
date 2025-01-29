# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
Vagrant.configure("2") do |config|
   config.vm.define "belousov03nginx" do |belousov03nginx|
      belousov03nginx.vm.box = "bento/ubuntu-24.04"      
      belousov03nginx.vm.host_name = "belousov03nginx"
      belousov03nginx.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = "2"
      end

      
      belousov03nginx.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
        s.inline = <<-SHELL
          echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
          echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
        SHELL
      end

   end
end