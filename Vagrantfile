Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  

  config.vm.define "packstack" do |packstack|

    config.vm.provider "virtualbox" do |vb|
      vb.memory = 16384
      vb.cpus = 8
      vb.name = "packstack"
    end

    packstack.vm.hostname = "packstack.dexter.com.br"
    packstack.vm.network "private_network", ip: "192.168.255.10", netmask: "255.255.255.0"
	
    packstack.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end


end
