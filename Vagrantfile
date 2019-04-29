# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |cluster|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
cluster.vm.define "k3sm" do |config|
  config.vm.box = "debian/stretch64"
  config.ssh.insert_key = true
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.default_nic_type = "virtio"
  end
  config.vm.hostname = "k3sm"
  config.vm.network :private_network,
    ip: "172.16.2.6",
    virtualbox__intnet: true,
    nic_type: "virtio"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.groups = {
      "tag_PrivNet_True" => ["k3sm"],
      "tag_Vagrant_True" => ["k3sm"],
      "tag_cluster_true" => ["k3sm"],
      "tag_master_true" => ["k3sm"],
      "tag_Name_k3sm" => ["k3sm"],
      "tag_PrivNet_True:vars" => {"place_authkeys" => "False",
                                   "masterip" => "172.16.2.6",
                                   "routeip" => "False"}
    }
  end
end

cluster.vm.define "k3s1" do |config|
  config.vm.box = "debian/stretch64"
  config.ssh.insert_key = true
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.default_nic_type = "virtio"
  end
  config.vm.hostname = "k3s1"
  config.vm.network :private_network,
    ip: "172.16.2.7",
    virtualbox__intnet: true,
    nic_type: "virtio"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.groups = {
      "tag_PrivNet_True" => ["k3s1"],
      "tag_Vagrant_True" => ["k3s1"],
      "tag_cluster_true" => ["k3s1"],
      "tag_node_true" => ["k3s1"],
      "tag_Name_k3s1" => ["k3s1"],
      "tag_PrivNet_True:vars" => {"place_authkeys" => "False",
                                   "masterip" => "172.16.2.6",
                                   "routeip" => "False"}
    }
  end
end

cluster.vm.define "k3s2" do |config|
  config.vm.box = "debian/stretch64"
  config.ssh.insert_key = true
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.default_nic_type = "virtio"
  end
  config.vm.hostname = "k3s2"
  config.vm.network :private_network, 
    ip: "172.16.2.8", 
    virtualbox__intnet: true,
    nic_type: "virtio"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.groups = {
      "tag_PrivNet_True" => ["k3s2"],
      "tag_Vagrant_True" => ["k3s2"],
      "tag_cluster_true" => ["k3s2"],
      "tag_node_true" => ["k3s2"],
      "tag_Name_k3s1" => ["k3s2"],
      "tag_PrivNet_True:vars" => {"place_authkeys" => "False",
                                   "masterip" => "172.16.2.6",
                                   "routeip" => "False"}
    }
  end
end

cluster.vm.define "k3s3" do |config|
  config.vm.box = "debian/stretch64"
  config.ssh.insert_key = true
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.default_nic_type = "virtio"
  end
  config.vm.hostname = "k3s3"
  config.vm.network :private_network, 
    ip: "172.16.2.9", 
    virtualbox__intnet: true,
    nic_type: "virtio"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.groups = {
      "tag_PrivNet_True" => ["k3s3"],
      "tag_Vagrant_True" => ["k3s3"],
      "tag_cluster_true" => ["k3s3"],
      "tag_node_true" => ["k3s3"],
      "tag_Name_k3s1" => ["k3s3"],
      "tag_PrivNet_True:vars" => {"place_authkeys" => "False",
                                   "masterip" => "172.16.2.6",
                                   "routeip" => "False"}
    }
  end
end

end
