# -*- mode: ruby -*-
# vi: set ft=ruby :

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

$create_ansible_vault_id = <<-SCRIPT
echo ">>> JUST FOR TESTING... - EXPOSING PASSWORD FILE <<<"
echo "1019" > /home/vagrant/pw
SCRIPT

$setup_ssh = <<-SCRIPT
SSH_PRIVATE_KEY=/home/vagrant/.ssh/id_rsa

if [ -f "$SSH_PRIVATE_KEY" ]; then
  echo "Skipping ssh-keygen - $SSH_PRIVATE_KEY already exists"
else
  sudo -u vagrant ssh-keygen -q -N '' -f $SSH_PRIVATE_KEY
fi

sudo apt install -y sshpass

deploy_key () {

  ping -c 1 -w 1 $1 > /dev/null
  RESULT=$?

  if [[ $RESULT -eq 0 ]]; then
  echo "Deploying SSH key on host $1"
    sudo -u vagrant sshpass -p vagrant ssh-copy-id vagrant@$1
  else
    echo "Host $1 is offline - skipping SSH key deployment"
  fi
}

deploy_key "debian"
deploy_key "rocky"
deploy_key "suse"
deploy_key "ubuntu"
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

$init_ansible_cfg = <<-SCRIPT
mkdir -p ~/ansible/projects/start/
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "bento/debian-11"
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "#{NETWORK_HOST_ANSIBLE}"
    ansible.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    ansible.vm.provision "shell", name: "setup_ssh", inline: $setup_ssh
    ansible.vm.provision "shell", name: "create_ansible_vault_id", inline: $create_ansible_vault_id
    ansible.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
    ansible.vm.provision "file", source: "projects/", destination: "~/ansible/projects"
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
