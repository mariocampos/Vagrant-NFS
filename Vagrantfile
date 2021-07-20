# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
(1..3).each do |i|
  config.vm.define "lab_#{i}" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname = "vm#{i}"
    node.vm.network "private_network", ip: "192.168.10.#{i}"
    node.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 256
    end
    end
  end
end
