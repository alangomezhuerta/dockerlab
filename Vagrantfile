Vagrant.configure("2") do |config|

	config.vm.define "vm1" do |vm1|
		vm1.vm.hostname = "vm1"
		vm1.vm.box = "generic/centos7"
		vm1.vm.network  "private_network", ip: "192.168.33.10"
		vm1.vm.provider "virtualbox" do |vb|
			vb.name = "vm1"
			vb.gui = false
			vb.memory = "512"
			vb.cpus = 1
		end
		vm1.vm.provision "shell", inline: <<-SHELL
			yum update -y
		SHELL
		#vm1.vm.provision "shell", run: "always", inline: <<-SHELL
		#	iptables -F
		#SHELL
		vm1.vm.provision "ansible" do | ansible |
			ansible.playbook = "playbook.yml"
		end
	end

	config.vm.define "vm2" do |vm2|
		vm2.vm.hostname = "vm2"
		vm2.vm.box = "generic/ubuntu1904"
		vm2.vm.network  "private_network", ip: "192.168.33.20"
		vm2.vm.provider "virtualbox" do |vb|
			vb.name = "vm2"
			vb.gui = false
			vb.memory = "512"
			vb.cpus = 1
		end
		vm2.vm.provision "shell", inline: <<-SHELL
			apt-get update -y
		SHELL
		vm2.vm.provision "shell", run: "always", inline: <<-SHELL
			iptables -F
		SHELL
    end

end

