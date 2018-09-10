# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.5"

  # 1台目管理マシン（マシン名：master）
  config.vm.define "master" do |atomic|
    atomic.vm.hostname = "master.k8s"
    atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2222
    atomic.vm.network "private_network", ip: "192.168.33.100", virtualbox__intnet: "k8s_hostnet"
    atomic.vm.network "public_network"
  
    atomic.vm.provider "virtualbox" do |box|
      box.gui = false
      box.memory = "4096"
      box.cpus = "3"

      box.customize [
        "modifyvm", :id,
        "--hwvirtex", "on",
        "--nestedpaging", "on",
        "--largepages", "on",
        "--ioapic", "on",
        "--pae", "on",
        "--paravirtprovider", "kvm",
      ]
    end
  end

  # 2台目 コンテナホスト（マシン名：node01）
  config.vm.define "node01" do |atomic|
    atomic.vm.hostname = "node01.k8s"
    atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2223
    atomic.vm.network "private_network", ip: "192.168.33.101", virtualbox__intnet: "k8s_hostnet"
    atomic.vm.network "public_network"
 
    atomic.vm.provider "virtualbox" do |box|
      box.gui = false
      box.memory = "4096"
      box.cpus = "3"

       box.customize [
        "modifyvm", :id,
        "--hwvirtex", "on",
        "--nestedpaging", "on",
        "--largepages", "on",
        "--ioapic", "on",
        "--pae", "on",
        "--paravirtprovider", "kvm",
      ]
    end
  end
  
  # 3台目 コンテナホスト（マシン名：node02）
  config.vm.define "node02" do |atomic|
    atomic.vm.hostname = "node02.k8s"
    atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2224
    atomic.vm.network "private_network", ip: "192.168.33.102", virtualbox__intnet: "k8s_hostnet"
    atomic.vm.network "public_network"
  
    atomic.vm.provider "virtualbox" do |box|
      box.gui = false
      box.memory = "4096"
      box.cpus = "3"

      box.customize [
        "modifyvm", :id,
        "--hwvirtex", "on",
        "--nestedpaging", "on",
        "--largepages", "on",
        "--ioapic", "on",
        "--pae", "on",
        "--paravirtprovider", "kvm",
      ]
    end
  end
  
  # ansible コンテナホスト（マシン名：ansible）
  config.vm.define "ansible" do |atomic|
    atomic.vm.hostname = "ansible.k8s"
    atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2225
    atomic.vm.network "private_network", ip: "192.168.33.103", virtualbox__intnet: "k8s_hostnet"
    atomic.vm.network "public_network"
  
    atomic.vm.provider "virtualbox" do |box|
      box.gui = false
      box.memory = "4096"
      box.cpus = "3"

      box.customize [
        "modifyvm", :id,
        "--hwvirtex", "on",
        "--nestedpaging", "on",
        "--largepages", "on",
        "--ioapic", "on",
        "--pae", "on",
        "--paravirtprovider", "kvm",
      ]
    end
  end
end
