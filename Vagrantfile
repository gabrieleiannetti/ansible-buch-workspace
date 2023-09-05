# -*- mode: ruby -*-
# vi: set ft=ruby :

#
# Bitte gegebenenfalls anpassen:
#
NETWORK_PREFIX = "192.168.56"

NETWORK_HOST_ANSIBLE = NETWORK_PREFIX + "." + "10"
NETWORK_HOST_DEBIAN  = NETWORK_PREFIX + "." + "20"
NETWORK_HOST_ROCKY   = NETWORK_PREFIX + "." + "30"
NETWORK_HOST_SUSE    = NETWORK_PREFIX + "." + "40"
NETWORK_HOST_UBUNTU  = NETWORK_PREFIX + "." + "50"

HOSTS = <<-STRING
127.0.0.1     localhost localhost.localdomain localhost4 localhost4.localdomain4
::1           localhost localhost.localdomain localhost6 localhost6.localdomain6

"#{NETWORK_HOST_ANSIBLE}" ansible
"#{NETWORK_HOST_DEBIAN}"  debian
"#{NETWORK_HOST_ROCKY}"   rocky
"#{NETWORK_HOST_SUSE}"    suse
"#{NETWORK_HOST_UBUNTU}"  ubuntu
STRING

$create_file_hosts = <<-SCRIPT
echo "#{HOSTS}" > /etc/hosts
SCRIPT

$install_ansible_debian = <<-SCRIPT
sudo apt update
sudo apt install -y ansible
SCRIPT

$install_ansible_centos = <<-SCRIPT
sudo yum install -y epel-release
sudo yum install -y ansible
SCRIPT

$install_ansible_suse = <<-SCRIPT
sudo zypper install -y ansible
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "bento/debian-11"
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "#{NETWORK_HOST_ANSIBLE}"
    ansible.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    ansible.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
  end

  config.vm.define "debian" do |debian|
    debian.vm.box = "bento/debian-11"
    debian.vm.hostname = "debian"
    debian.vm.network :private_network, ip: "#{NETWORK_HOST_DEBIAN}"
    debian.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    debian.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
  end

  config.vm.define "rocky" do |rocky|
    rocky.vm.box = "bento/rockylinux-8"
    rocky.vm.hostname = "rocky"
    rocky.vm.network :private_network, ip: "#{NETWORK_HOST_ROCKY}"
    rocky.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    rocky.vm.provision "shell", name: "install_ansible_centos", inline: $install_ansible_centos

  end

  config.vm.define "suse" do |suse|
    suse.vm.box = "bento/opensuse-leap-15"
    suse.vm.hostname = "suse"
    suse.vm.network :private_network, ip: "#{NETWORK_HOST_SUSE}"
    suse.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    suse.vm.provision "shell", name: "install_ansible_suse", inline: $install_ansible_suse
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-20.04"
    ubuntu.vm.hostname = "ubuntu"
    ubuntu.vm.network :private_network, ip: "#{NETWORK_HOST_UBUNTU}"
    ubuntu.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    ubuntu.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
  end

end
