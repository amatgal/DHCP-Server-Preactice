# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"

  # Servidor DHCP

  config.vm.define "server" do |server|
    server.vm.hostname = "server"
    # Adaptador con acceso al host (para Internet y descargas)
    server.vm.network "private_network", ip: "192.168.56.10"
    # Adaptador red interna (para DHCP)
    server.vm.network "private_network", ip: "192.168.57.10", virtualbox__intnet: "dhcpnet"
    server.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
  end


  # Cliente 1

  config.vm.define "c1" do |c1|
    c1.vm.hostname = "c1"
    c1.vm.network "private_network", type: "dhcp", virtualbox__intnet: "dhcpnet"
    c1.vm.provider "virtualbox" do |vb|
      vb.memory = 256
      vb.cpus = 1
    end
  end

  # Cliente 2

  config.vm.define "c2" do |c2|
    c2.vm.hostname = "c2"
    c2.vm.network "private_network", type: "dhcp", virtualbox__intnet: "dhcpnet"
    c2.vm.provider "virtualbox" do |vb|
      vb.memory = 256
      vb.cpus = 1
    end
  end
end
