# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # use ubuntu 22.04 as the base box
    # config.vm.box = "generic/ubuntu2204"
    config.vm.box = "crystax/ubuntu2404"

    config.vm.synced_folder ".", "/vagrant", disabled: true
    # contain our CCA modules for debug purpose
    # config.vm.synced_folder "./cc_modules", "/home/vagrant/cc_modules", type: 'nfs' , nfs_version: 3, nfs_udp: false
    # config.vm.synced_folder "./scripts", "/home/vagrant/scripts", type: 'nfs' , nfs_version: 3, nfs_udp: false
    config.vm.synced_folder "./aurora", "/home/vagrant/aurora", type: 'rsync'
    config.vm.synced_folder "./PCC-Uspace", "/home/vagrant/pcc-uspace", type: 'rsync'
    config.vm.synced_folder "./scripts", "/home/vagrant/scripts", type: 'rsync'
    # config.vm.synced_folder ".","/vagrant_data",type:'9p',accessmode:"squash",mount:"true"

    # ssh setting
    # config.ssh.private_key_path = "~/.ssh/id_rsa"
    # config.ssh.forward_agent = true
    config.ssh.insert_key = true
    config.ssh.username = 'vagrant'
    config.ssh.password = 'vagrant'

    config.vm.network "private_network", ip: "192.168.121.5"
    config.vm.define "vm-aurora"

    #disk size:50GB 
    config.vm.disk :disk, size: "50GB", primary: true
    config.vm.provider:"libvirt" do |lv|
      # Customize the amount of memory on the VM:
      # lv.management_network_pci_bus = "0x00"
      # lv.management_network_pci_slot = "0x05"
      lv.machine_virtual_size = 128
      lv.memory = 32768
      lv.cpus = 10
      lv.cpu_mode = "host-passthrough"
    end

    # config.vm.provision "file", source: "./kern_src", destination: "/home/vagrant/kern_src"
    # config.vm.provision "file", source: "./setup-vm.sh", destination: "/home/vagrant/setup-vm.sh"
    # config.vm.provision "shell", inline: "scripts/setup orca-vm"
    config.vm.provision "shell", inline: "/home/vagrant/scripts/setup", privileged: false
  end
