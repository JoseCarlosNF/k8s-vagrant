# -*- mode: ruby -*-
# vi: set ft=ruby :
IMAGEM_SISTEMA = "centos/7"
WORKER_NODES = 2

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  # Configurações do Master Node
  config.vm.define "k8s-master" do |master|
    master.vm.box = IMAGEM_SISTEMA
    master.vm.network = "private_network", ip: "192.168.33.10"
    master.vm.hostname = "k8s-master"

    master.vm.provider "virtualbox" do |machine|
      machine.memory = 2048
      machine.cpus = 2
    end

    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "Playbooks/master-playbook.yml"
      ansible.extra_vars = {
          node_ip: "192.168.50.10",
      }
    end
  end

  (1..WORKER_NODES).each do |i|
    config.vm.define "node-#{i}" do |node|
      node.vm.box = IMAGEM_SISTEMA
      node.vm.network = "private_network", ip: "192.168.33.#{i + 10}"
      node.vm.hostname = "node-#{i}"

      master.vm.provider "virtualbox" do |machine|
        machine.memory = 512
        machine.cpus = 1
      end

      node.vm.provision "ansible" do |ansible|
        ansible.playbook = "Playbooks/node-playbook.yml"
        ansible.extra_vars = {
          node_ip: "192.168.33.#{i + 10}"
        }
      end
    end
  end
end
