# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
  
  # First VM
  config.vm.define "hadoop1" do |hadoop1|
    hadoop1.vm.hostname = "hadoop1"
    hadoop1.vm.network "private_network", ip: "192.168.33.10"
    hadoop1.vm.provider "virtualbox" do |vb|
      vb.memory = "3072"
      vb.cpus = 2
    end
    hadoop1.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y openjdk-8-jdk
      wget https://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
      tar -xzf hadoop-3.3.1.tar.gz
      mv hadoop-3.3.1 /usr/local/hadoop
      echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
      echo "export PATH=$PATH:$HADOOP_HOME/bin" >> ~/.bashrc
      source ~/.bashrc
    SHELL
  end

  # Second VM
  config.vm.define "hadoop2" do |hadoop2|
    hadoop2.vm.hostname = "hadoop2"
    hadoop2.vm.network "private_network", ip: "192.168.33.11"
    hadoop2.vm.provider "virtualbox" do |vb|
      vb.memory = "3072"
      vb.cpus = 2
    end
    hadoop2.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y openjdk-8-jdk
      wget https://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
      tar -xzf hadoop-3.3.1.tar.gz
      mv hadoop-3.3.1 /usr/local/hadoop
      echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
      echo "export PATH=$PATH:$HADOOP_HOME/bin" >> ~/.bashrc
      source ~/.bashrc
    SHELL
  end

  # Third VM
  config.vm.define "hadoop3" do |hadoop3|
    hadoop3.vm.hostname = "hadoop3"
    hadoop3.vm.network "private_network", ip: "192.168.33.12"
    hadoop3.vm.provider "virtualbox" do |vb|
      vb.memory = "3072"
      vb.cpus = 2
    end
    hadoop3.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y openjdk-8-jdk
      wget https://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
      tar -xzf hadoop-3.3.1.tar.gz
      mv hadoop-3.3.1 /usr/local/hadoop
      echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
      echo "export PATH=$PATH:$HADOOP_HOME/bin" >> ~/.bashrc
      source ~/.bashrc
    SHELL
  end

  # Configure Hadoop
  config.vm.define "configure-hadoop" do |configure|
    configure.vm.hostname = "configure"
    configure.vm.network "private_network", ip: "192.168.33.13"
    configure.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 1
    end
    configure.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y rsync
      sudo rsync -av /vagrant/hadoop-configuration/ /usr/local/hadoop/etc/hadoop/
    SHELL
  end

end


