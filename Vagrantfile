# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("4") do |config|
  config.vm.box = "bento/centos-7.5"

  # auto up all
  config.vm.define "k8s_master"
  config.vm.define "k8s_node1"
  config.vm.define "k8s_node2"
  config.vm.define "k8s_vagrant", autostart: false

  config.vm.provider "k8s_master" do |k8s_master|
    k8s_master.hostname = "k8s_master"
    k8s_master.name = "k8s_master"
    k8s_master.gui = true
    k8s_master.memory = "4096"
    k8s_master.cpus = "3"

    # vm management network
    k8s_master.vm.network "private_network", ip: "192.168.33.5", virtualbox__intnet: "k8s_vm_management_network"

    k8s_master.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]

  end

  config.vm.provider "k8s_node1" do |k8s_node1|
    k8s_node1.hostname = "k8s_node1"
    k8s_node1.name = "k8s_node1"
    k8s_node1.gui = true
    k8s_node1.memory = "4096"
    k8s_node1.cpus = "3"

    k8s_node1.vm.network "private_network", ip: "192.168.33.5", virtualbox__intnet: "k8s_vm_management_network"

    k8s_node1.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]

  end

 config.vm.provider "k8s_node2" do |k8s_node2|
    k8s_node2.hostname = "k8s_node2"
    k8s_node2.name = "k8s_node2"
    k8s_node2.gui = true
    k8s_node2.memory = "4096"
    k8s_node2.cpus = "3"

    k8s_node2.vm.network "private_network", ip: "192.168.33.5", virtualbox__intnet: "k8s_vm_management_network"

    k8s_node2.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]

  end  
  
 config.vm.provider "k8s_ansible" do |k8s_ansible|
    k8s_ansible.hostname = "k8s_ansible"
    k8s_ansible.name = "k8s_ansible"
    k8s_ansible.gui = true
    k8s_ansible.memory = "4096"
    k8s_ansible.cpus = "3"

    k8s_ansible.vm.network "private_network", ip: "192.168.33.5", virtualbox__intnet: "k8s_vm_management_network"

    k8s_ansible.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]

    k8s_ansible.vm.provision "shell", inline: <<-SHELL
      yum update
      yum install -y epel-release
      yum install -y ansible
      yum install -y https://centos7.iuscommunity.org/ius-release.rpm
      yum install -y python36u python36u-libs python36u-devel python36u-pip
    SHELL

  end
  
  config.vm.provision "shell", inline: <<-SHELL
    yum update
    yum install vim
  SHELL
end
