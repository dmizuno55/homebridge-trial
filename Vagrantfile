# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ARTACK/debian-jessie"

  config.vm.network "private_network", ip: "192.168.33.11"
  config.vm.network "forwarded_port", guest:51826, host:51826

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
    vb.customize ["modifyvm", :id, "--usbxhci", "off"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./playbooks/site.yml"
    ansible.inventory_path="./playbooks/hosts"
    ansible.verbose = "vvvv"
    ansible.limit = "homebridge"
  end

  config.ssh.forward_agent = true
end
