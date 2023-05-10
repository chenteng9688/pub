# -*- mode: ruby -*-
# vi: set ft=ruby :

# Set VMs name
nodes = [
  { :name => "hadoop-master", :ip => "192.168.33.10", :ram => "2048", :cpu => "2" },
  { :name => "hadoop-slave1", :ip => "192.168.33.11", :ram => "2048", :cpu => "1" },
  { :name => "hadoop-slave2", :ip => "192.168.33.12", :ram => "2048", :cpu => "1" },
  { :name => "hadoop-slave3", :ip => "192.168.33.13", :ram => "2048", :cpu => "1" },
  { :name => "hbase-master", :ip => "192.168.33.14", :ram => "2048", :cpu => "2" },
  { :name => "hbase-slave1", :ip => "192.168.33.15", :ram => "2048", :cpu => "1" },
  { :name => "hbase-slave2", :ip => "192.168.33.16", :ram => "2048", :cpu => "1" },
  { :name => "spark-master", :ip => "192.168.33.17", :ram => "2048", :cpu => "2" },
  { :name => "spark-slave1", :ip => "192.168.33.18", :ram => "2048", :cpu => "1" },
  { :name => "spark-slave2", :ip => "192.168.33.19", :ram => "2048", :cpu => "1" },
  { :name => "zookeeper-server", :ip => "192.168.33.20", :ram => "2048", :cpu => "1" },
  { :name => "elasticsearch-node1", :ip => "192.168.33.21", :ram => "2048", :cpu => "2" },
  { :name => "elasticsearch-node2", :ip => "192.168.33.22", :ram => "2048", :cpu => "1" }
]

Vagrant.configure("2") do |config|

  # Loop through each node to configure the VM
  nodes.each do |node|

    # Set the box for the VM
    config.vm.define node[:name] do |box|
      box.vm.box = "ubuntu/bionic64"

      # Configure VM settings
      box.vm.hostname = node[:name]
      box.vm.network "private_network", ip: node[:ip]

      # Set CPU and memory
      box.vm.provider "virtualbox" do |vb|
        vb.memory = node[:ram]
        vb.cpus = node[:cpu]
      end

      # Copy files and run scripts
      box.vm.synced_folder ".", "/vagrant", disabled: true
      box.vm.provision "shell", path: "scripts/common.sh"
      box.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
      SHELL
    end
  end
end
