# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.hostname = "gitlab.local.dev"

    config.vm.network :private_network, ip: "10.0.0.10"
    config.vm.network :forwarded_port, guest: 80, host: 8080
    config.vm.network :forwarded_port, guest: 22, host: 2222
    config.vm.network :forwarded_port, guest: 443, host: 443

    config.vm.provider "virtualbox" do |vb|
        vb.name = "GitLab Server"
        vb.memory = "4096"
        vb.cpus = "2"
        vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
        
    end

    config.vm.provision :docker
    config.vm.provision "shell", path: "install_gitlab.sh"
end
