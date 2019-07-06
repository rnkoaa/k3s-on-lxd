# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |v|
    v.memory = 8192
    v.cpus = 5
  end

  # config.vm.provision "file" source: "./.ssh/id_rsa.pub" destination: "/home/vagrant/.ssh/authorized_keys"

  # add our current ssh public keys to the authorized keys
  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("./.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
    SHELL
  end

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    echo "==> Shell Provisioning"

    VAGRANT_SSH_DIRECTORY="/home/vagrant/.ssh"
    if [ ! -d "$VAGRANT_SSH_DIRECTORY" ]; then
      mkdir /home/vagrant/.ssh
    fi

    file="/home/vagrant/.vimrc"
    if [ -f "$file" ]
    then
        echo ".vimrc exists, will not download again."
    else
      wget -q -O /home/vagrant/.vimrc https://raw.githubusercontent.com/amix/vimrc/master/vimrcs/basic.vim
    fi
    SHELL
end
