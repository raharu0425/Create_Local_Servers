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

  # web01
  config.vm.define "web" do |web|
    web.vm.box = "centos67_x84"
    # 仮装マシンの設定
    web.vm.network "private_network", ip: "192.168.185.101"
    web.vm.network "forwarded_port", guest: 22, host: 2001
    # 実行権限を変更する
    web.vm.synced_folder "./sync/dbapi", "/vagrant/sync/dbapi", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    web.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "128"
    end
  end

  # webadmin
  config.vm.define "admin" do |admin|
    admin.vm.box = "centos67_x84"
    # 仮装マシンの設定
    admin.vm.network "private_network", ip: "192.168.185.103"
    admin.vm.network "forwarded_port", guest: 22, host: 2003
    # 実行権限を変更する
    admin.vm.synced_folder "./files", "/vagrant/files", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    admin.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "128"
    end
  end

  # redis
  config.vm.define "redis" do |redis|
    redis.vm.box = "centos67_x84"
    # 仮装マシンの設定
    redis.vm.network "private_network", ip: "192.168.185.104"
    redis.vm.network "forwarded_port", guest: 22, host: 2004
    # 実行権限を変更する
    #redis.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    redis.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "128"
    end
  end

  # db_master
  config.vm.define "dbm" do |dbm|
    dbm.vm.box = "centos67_x84"
    # 仮装マシンの設定
    dbm.vm.network "private_network", ip: "192.168.185.105"
    dbm.vm.network "forwarded_port", guest: 22, host: 2005
    # 実行権限を変更する
    #redis.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    dbm.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "128"
    end
  end

  # db_slave
  config.vm.define "dbs" do |dbs|
    dbs.vm.box = "centos67_x84"
    # 仮装マシンの設定
    dbs.vm.network "private_network", ip: "192.168.185.106"
    dbs.vm.network "forwarded_port", guest: 22, host: 2006
    # 実行権限を変更する
    #redis.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    dbs.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "128"
    end
  end

  # server_maanger（管理サーバー）
  config.vm.define "sm" do |sm|
    sm.vm.box = "centos67_x84"
    # 仮装マシンの設定
    sm.vm.network "private_network", ip: "192.168.185.107"
    sm.vm.network "forwarded_port", guest: 22, host: 2007
    # 実行権限を変更する
    #redis.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=777','fmode=777']
    # GUIの有効化やメモリ数
    sm.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "512"
    end
  end

  # Ansibleの構造を作成
  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "provisioning/site.yml"
  #  ansible.inventory_path = "provisioning/hosts"
  #  ansible.limit = 'all'
  #end
end
