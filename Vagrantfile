Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 9000, host: 9000
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  config.vm.provider "virtualbox" do |vb|
    vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    vb.memory = "8096"
    vb.cpus = 4
  end
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision/vagrant.yml"
    ansible.extra_vars = {
      ansible_python_interpreter: '/usr/bin/python3'
    }
  end
end
