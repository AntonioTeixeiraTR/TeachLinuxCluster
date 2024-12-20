# -*- mode: ruby -*-
# vi: set ft=ruby :

#VAGRANTFILE_API_VERSION = "2"

# to create a extra disk for the VM use the below command before starting the vm :     ( If using libvirt-kvm you hava to adapt the command to qemu-img and change the vagrant file )
#
# vboxmanage createhd --filename /home/antonioteixeira/software/git-repos/Linux-Trainning/ISCSI_CLUSTER/tmp/20Giscsi.vdi --size 20000
# config.vm.network "private_network", ip: "172.16.0.100" <=== This line causes alll 5 NICs to be configured ===>
#file_to_disk = './tmp/20G-iscsi.vdi' ## This is to use with the customize lines   ---> do not work very well tough

Vagrant.configure("2") do |config|
  config.ssh.insert_key = true
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.provider :vbox do |vbox|
  config.vm.box_version = "9.3.20231118"
  vbox.memory = 8192
  # FOR THE PERSISTENT STORAGE BELOW you need the following plugin installed : vagrant-persistent-storage
  end

# ISCSI SERVER
  config.vm.define "iscsi" do |iscsi|
    iscsi.vm.hostname = "iscsi"
    iscsi.persistent_storage.enabled = true
    iscsi.persistent_storage.location = './tmp/sdc.vdi'
    iscsi.persistent_storage.size = 20000
    iscsi.persistent_storage.diskdevice = '/dev/sdb'
    iscsi.vm.network "private_network", :type => 'static', ip: "172.17.0.100", :name => 'vboxnet0', :adapter => 2
    iscsi.vm.box = "almalinux/9"
  end


  config.vm.provision "ansible" do |a|
    a.verbose = "v"
    a.playbook = "iscsi_config.yml"
  end

#  CLUSTER NODE1
   config.vm.define "node1" do |node1|
     node1.vm.hostname = "node1"
     node1.vm.network "private_network", :type => 'static', ip: "172.17.0.101", :name => 'vboxnet0', :adapter => 2
     node1.vm.network "private_network", :type => 'static', ip: "192.168.200.101", :name => 'vboxnet0', :adapter => 3
     node1.vm.network "private_network", :type => 'static', ip: "192.168.30.101", :name => 'vboxnet0', :adapter => 4
     node1.vm.box = "almalinux/9"
   end

 config.vm.provision "ansible" do |b|
    b.verbose = "v"
    b.playbook = "initiator_config_1.yml"
  end


#  CLUSTER NODE2
   config.vm.define "node2" do |node2|
     node2.vm.hostname = "node2"
     node2.vm.network "private_network", :type => 'static', ip: "172.17.0.102", :name => 'vboxnet0', :adapter => 2
     node2.vm.network "private_network", :type => 'static', ip: "192.168.200.102", :name => 'vboxnet0', :adapter => 3
     node2.vm.network "private_network", :type => 'static', ip: "192.168.30.102", :name => 'vboxnet0', :adapter => 4
     node2.vm.box = "almalinux/9"
   end

  config.vm.provision "ansible" do |c|
    c.verbose = "v"
    c.playbook = "initiator_config_2.yml"
  end


end
