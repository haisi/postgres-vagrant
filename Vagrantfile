# the ip address where the vm can be accessed from the host
vm_ip                   = "172.16.1.2"
host_name               = "vagrant.me"

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.provision :shell, :path => "scripts/setup.sh"
    config.vm.network :forwarded_port, host: 8080, guest: 8080
    config.vm.network :forwarded_port, host: 9000, guest: 9000
	# PostgreSQL Server port forwarding
	config.vm.network :forwarded_port, host: 5432, guest: 5432
	config.vm.network :forwarded_port, host: 15432, guest: 15432
    config.ssh.insert_key = true
    config.vm.synced_folder '.', '/vagrant'
	
	config.vm.network :private_network, ip: vm_ip
	config.vm.hostname = host_name

    config.vm.provider :virtualbox do |vb|
        # vb.gui = true
        # Use VBoxManage to customize the VM. For example to change memory:
        vb.customize ["modifyvm", :id, "--name", "jhipster-devbox"]
        vb.customize ["modifyvm", :id, "--memory", "2048"]
        vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
        vb.customize ['modifyvm', :id, '--draganddrop', 'bidirectional']
    end
end