Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  

  config.vm.define "packstack" do |packstack|

    config.vm.provider "virtualbox" do |vb|
      vb.memory = 8192
      vb.cpus = 2
      vb.name = "packstack"
    end

    packstack.vm.hostname = "packstack.dexter.com.br"
    packstack.vm.network "private_network", ip: "0.0.0.0", auto_network: true
    packstack.vm.network "forwarded_port", guest: 80, host: 8080
    packstack.vm.network "forwarded_port", guest: 6080, host: 6080

    packstack.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end

##
## Descomentar o que vem abaixo caso não possua o Ansible instalado no host.
##

#packstack.vm.provision "file", source: "./packstack-answers.txt", destination:"/tmp/packstack-answers.txt"
#packstack.vm.provision "shell", inline: <<-SHELL
#  
#  dnf install network-scripts -y
#
#  systemctl disable firewalld
#  systemctl stop firewalld
#  systemctl disable NetworkManager
#  systemctl stop NetworkManager
#  systemctl enable network
#  systemctl start network
#  
#  dnf update -y --exclude=kernel*
#  dnf config-manager --enable PowerTools
#  dnf config-manager --disable epel,epel-modular
#  dnf install -y centos-release-openstack-train
#  dnf update -y --exclude=kernel*
#  dnf install -y openstack-packstack
#  packstack --answer-file /tmp/packstack-answers.txt
# 
#SHELL


  end


end
