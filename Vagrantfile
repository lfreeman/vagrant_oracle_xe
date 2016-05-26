# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.ssh.insert_key = false

  config.vm.define :db do |m|
    m.vm.hostname = "oracle"
    m.vm.box = "ubuntu/trusty64"
    m.vm.network  "forwarded_port", guest: 1521, host: 1521, auto_correct: true
    m.vm.network :private_network, ip: "192.168.61.10"
    m.vm.provider "virtualbox" do |v|
      v.memory = 1024

      # m.vm.provision :ansible do |ansible|
      #   ansible.limit = "all"
      #   ansible.playbook = "ansible/playbook.yml"
      # end
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end
end
