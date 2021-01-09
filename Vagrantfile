# -*- mode: ruby -*-
# vim: set ft=ruby :
# RR

MACHINES=[
  {
    :box_name => "centos/7",
    :hostname => "web",
    :ip => "192.168.100.10"

  }
]

Vagrant.configure(2) do |config|
    MACHINES.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box_name]
            node.vm.hostname = machine[:hostname]
            node.vm.network "private_network", ip: machine[:ip]
            node.vm.provider "virtualbox" do |v|
              v.memory = 1024
            end
            node.vm.provision "ansible" do |ansible|
              ansible.playbook = "play.yml"
              ansible.verbose = "v"
            end
        end
    end
end

