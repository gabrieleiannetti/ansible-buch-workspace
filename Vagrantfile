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

$configure_ssh_private_key = <<-SCRIPT
echo "-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAx8pDSj/B27WZsP68d+TyuV+1wlJlT1YxYAeMbW0LVx0SV8An/7RG
wEKpyoIBKfgbnkiO+I5Y13bRpVscm0DQO76ALpu1hkNw7kh0M7i6AxlwBaWoVCvfDyzz02
kPsvN6sJqm9XIQ7Sqwk8JZKZPorZBKzly4u5f5cnAqYp4tVFQssm8E21XjyfJCUvN2OEFZ
fuYpWUoehff7zBYSYOHIbKta+OqXu4/ulZbJpp8rlaTQPesN/2uZVQ8nykryVO1PuMVueC
yt1Bxz2DxKrrKcvD9aaWI2jYtcP5qwVn5EnkQs76SPwflW9HVL7xJ4EZtM5WWqxOXXFSb5
oadT32knTQ//r1XYBOvjHvXY8VPy9xMdGJnzZZwgQxnRaqUyfb7SsoiE2L3CDXwKu3W4Ey
3lfY9TVFb190zSYbw/7vG+z0jDZtolVyuWkBcPzVt5MH43ATHWhfLilK7ByY+wFF7BuMuk
1oYe8VNqhCmY6qgtsPioOJ1OPzGUs3FGHDs5mvzxAAAFiNLzyr3S88q9AAAAB3NzaC1yc2
EAAAGBAMfKQ0o/wdu1mbD+vHfk8rlftcJSZU9WMWAHjG1tC1cdElfAJ/+0RsBCqcqCASn4
G55IjviOWNd20aVbHJtA0Du+gC6btYZDcO5IdDO4ugMZcAWlqFQr3w8s89NpD7LzerCapv
VyEO0qsJPCWSmT6K2QSs5cuLuX+XJwKmKeLVRULLJvBNtV48nyQlLzdjhBWX7mKVlKHoX3
+8wWEmDhyGyrWvjql7uP7pWWyaafK5Wk0D3rDf9rmVUPJ8pK8lTtT7jFbngsrdQcc9g8Sq
6ynLw/WmliNo2LXD+asFZ+RJ5ELO+kj8H5VvR1S+8SeBGbTOVlqsTl1xUm+aGnU99pJ00P
/69V2ATr4x712PFT8vcTHRiZ82WcIEMZ0WqlMn2+0rKIhNi9wg18Crt1uBMt5X2PU1RW9f
dM0mG8P+7xvs9Iw2baJVcrlpAXD81beTB+NwEx1oXy4pSuwcmPsBRewbjLpNaGHvFTaoQp
mOqoLbD4qDidTj8xlLNxRhw7OZr88QAAAAMBAAEAAAGAaaC1LNdCjf+YLyyuxhCkh39joE
Zhy609U5EKHHxvZ3I2VXCBdT6BvXpBPJC5PtAvAeNIu36+18O5GVxvZmHA9iVErd+i/EZB
ualSzlmW9raHNGUd9spvFx3kF1zPcQQrVJ2fMdtJuao9SxGQhFvvw3urISmCfaPevTMyJY
uNWa1bKEdr4O6rDQTpLeQMF7ftMhtLtyppstimJoNw2gnlJhb+dOXKrN5u/GWJXW9/4pEN
i/7vGqBvo7nshpZTQrVn5ojXNQwsrYJZWGCupxp3RZplTqe/YFp9d1/GKThJB07f8O4Wgh
D/ypQ0HhaLqzUlSQLexfxx+v0IYaAPwfKn+QPGwuou9q0LT1klOhcxBe16kkKiEjV+LzGa
hYhA4+3bL/GkQz4yww7EczZCg79ZZb7Xa4tXJMUesjTJdvHkMFEzcTXbOSgK88OgI/Xmec
cN/wfZ0WGwKBUFIR4nzGnFwfyfC8OxLjviJZfCxHBRGt5hDq5xYMEUvO5IvRCq9kJFAAAA
wB1Lwt/tGq3gUlw2Oo/L+IXDkMgVlb9dNNm6uNlQhiKuU/hmpoM7ypbeo+to9cti3xd2ws
Tr14TPIWLPQSD2HAlh/pDUxlnpRwSu0hoHNmj1a9zQO+CK37DtZ4hAstXKVI9REwKfa20N
Wl8KOxrBRnVKrmyCIbbzEuBl0cUagdaTwYghBOseWV1grupo9gvyhLWau6rdUWI7kelFM9
lZOXji5+/pQigdkchqXLTZM501ancfAxtMyhiOHEr4UD4w+AAAAMEA5+v0FlJB7y43gJUn
OTbAlcQZG6nOM406m8d9l4zWLETioNdt0Cb/cJ1lPfAGp37yGXNAYZpAwopDkZB5Vc3WuQ
pe/XuITNloCMs7liQ0JjThz531au2XYaQlVzH1E53S5XsOrqmtruij4JiXO0XnKSG6Wyit
QujgGEykKTgrwrHatZJHXXGuL0x04MtTbhZZWImdW8t7PTrl0O3HGTdii3yLT3Y86X0siL
hEsDBItxEv1FxT9kqrl9/birqJc7zfAAAAwQDciE+ru/Qs3v6baz2diQ2Gv0QLV7zhmZs/
DZePdGVh/MET1Zx47eEgcKxFFPuyfwAtUTes0qPAZ0Su6+FIddWG9CuuCnCxxRSKVKKyPZ
6ynclUIcQ17M72OPqN6gq8fxbiPmSvLyDeYitTsChA/f64fpyc7IHvKbzBcR4+6fPZpq9X
QizB+LVJ8x3KRfcF25OzU7scGtjKuYt+90THChF13C47/37z9i/JHR0Ufc76x6JhHCz7fZ
QD/7os84K+sC8AAAAPdmFncmFudEBhbnNpYmxlAQIDBA==
-----END OPENSSH PRIVATE KEY-----" > /home/vagrant/.ssh/id_rsa
SCRIPT

$configure_ssh_public_key = <<-SCRIPT

SSH_PUB_KEY="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHykNKP8HbtZmw/rx35PK5X7XCUmVPVjFgB4xtbQtXHRJXwCf/tEbAQqnKggEp+BueSI74jljXdtGlWxybQNA7voAum7WGQ3DuSHQzuLoDGXAFpahUK98PLPPTaQ+y83qwmqb1chDtKrCTwlkpk+itkErOXLi7l/lycCpini1UVCyybwTbVePJ8kJS83Y4QVl+5ilZSh6F9/vMFhJg4chsq1r46pe7j+6VlsmmnyuVpNA96w3/a5lVDyfKSvJU7U+4xW54LK3UHHPYPEquspy8P1ppYjaNi1w/mrBWfkSeRCzvpI/B+Vb0dUvvEngRm0zlZarE5dcVJvmhp1PfaSdND/+vVdgE6+Me9djxU/L3Ex0YmfNlnCBDGdFqpTJ9vtKyiITYvcINfAq7dbgTLeV9j1NUVvX3TNJhvD/u8b7PSMNm2iVXK5aQFw/NW3kwfjcBMdaF8uKUrsHJj7AUXsG4y6TWhh7xU2qEKZjqqC2w+Kg4nU4/MZSzcUYcOzma/PE="

AUTHORIZED_KEYS="/home/vagrant/.ssh/authorized_keys"

# if grep -q ${SSH_PUB_KEY} ${AUTHORIZED_KEYS}; then
#   echo FOUND
# else
#   echo NOT-FOUND
# fi
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "bento/debian-11"
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "#{NETWORK_HOST_ANSIBLE}"
    ansible.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    ansible.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
    ansible.vm.provision "shell", name: "configure_ssh_private_key", inline: $configure_ssh_private_key
  end

  config.vm.define "debian" do |debian|
    debian.vm.box = "bento/debian-11"
    debian.vm.hostname = "debian"
    debian.vm.network :private_network, ip: "#{NETWORK_HOST_DEBIAN}"
    debian.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    debian.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
    debian.vm.provision "shell", name: "configure_ssh_public_key", inline: $configure_ssh_public_key
  end

  config.vm.define "rocky" do |rocky|
    rocky.vm.box = "bento/rockylinux-8"
    rocky.vm.hostname = "rocky"
    rocky.vm.network :private_network, ip: "#{NETWORK_HOST_ROCKY}"
    rocky.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    rocky.vm.provision "shell", name: "install_ansible_centos", inline: $install_ansible_centos
    rocky.vm.provision "shell", name: "configure_ssh_public_key", inline: $configure_ssh_public_key
  end

  config.vm.define "suse" do |suse|
    suse.vm.box = "bento/opensuse-leap-15"
    suse.vm.hostname = "suse"
    suse.vm.network :private_network, ip: "#{NETWORK_HOST_SUSE}"
    suse.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    suse.vm.provision "shell", name: "install_ansible_suse", inline: $install_ansible_suse
    suse.vm.provision "shell", name: "configure_ssh_public_key", inline: $configure_ssh_public_key
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-20.04"
    ubuntu.vm.hostname = "ubuntu"
    ubuntu.vm.network :private_network, ip: "#{NETWORK_HOST_UBUNTU}"
    ubuntu.vm.provision "shell", name: "create_file_hosts", inline: $create_file_hosts
    ubuntu.vm.provision "shell", name: "install_ansible_debian", inline: $install_ansible_debian
    ubuntu.vm.provision "shell", name: "configure_ssh_public_key", inline: $configure_ssh_public_key
  end

end
