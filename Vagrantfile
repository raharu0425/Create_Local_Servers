# --*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.

  # local_server
  config.vm.define "server" do |server|
    server.vm.box = "centos67_x84"
    # 仮装マシンのIPアドレス
    server.vm.network "private_network", ip: "192.168.183.110"
    server.vm.network "forwarded_port", guest: 22, host: 2210
    # 実行権限を変更する
    server.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    server.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "1024"
    end
  end

  # Ansibleの構造を作成
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
    ansible.inventory_path = "provisioning/hosts"
    ansible.limit = 'all'
  end
end
