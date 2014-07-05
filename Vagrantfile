# -*- mode: ruby -*-
# vi: set ft=ruby :

IP_ADDRESS = "192.168.33.101"
VHOST      = "deploy.#{IP_ADDRESS}.xip.io"

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu-trusty-amd64-20140705"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/20140705/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.network "private_network", ip: IP_ADDRESS
  config.ssh.forward_agent = true

  #Installing Dokku
  #if vargrant ssh does not work in windows, run on guest the command.
  config.vm.provision :shell, :inline => <<-EOS

    # install
    wget -qO- https://raw.github.com/progrium/dokku/v0.2.3/bootstrap.sh | sudo DOKKU_TAG=v0.2.3 bash

    # set vhost
    sudo echo #{VHOST} > /home/dokku/VHOST

    # config sshcomand ( grep is skip vagrunt comment )
    grep ^ssh-rsa ~/.ssh/authorized_keys | sudo sshcommand acl-add dokku vagrant

  EOS
end