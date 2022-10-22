# -*- mode: ruby -*-
# vi: set ft=ruby :
# To enable zsh, please set ENABLE_ZSH env var to "true" before launching vagrant up 
#   + On windows => $env:ENABLE_ZSH="true"
#   + On Linux  => export ENABLE_ZSH="true"

Vagrant.configure("2") do |config|
    config.vm.define "webapp-server" do |ws|
        ws.vm.box = "geerlingguy/debian10"
        # ws.vm.network "private_network", type: "dhcp"
        ws.vm.hostname = "webapp-server"
        ws.vm.provider "virtualbox" do |vb|
            vb.name = "webapp-server"
            vb.memory = 512
            vb.cpus = 2
        end

        #RUN ONCE
        # ws.vm.provision "shell", inline: <<-SHELL
        #     sudo apt-get update
        #     sudo apt-get install software-properties-common
        #     sudo apt-get install python 3.8
        #  SHELL
        
        # Provision Websevers
        ws.vm.provision "ansible_local" do |ansible|
            ansible.install = true
            ansible.version = "latest"
            ansible.sudo = true
            ansible.playbook = "deploy-webapp.yml"
            # ansible.install = true
            ansible.verbose = "v"
        end
    end
end