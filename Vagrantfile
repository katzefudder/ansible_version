Vagrant.configure("2") do |config|
    config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    config.vm.define "192.168.1.101" do |master|
        master.vm.box = "wittman/centos-7.2-ansible"
        master.ssh.insert_key = false
        master.vm.network :private_network, ip: "192.168.1.101"
        master.vm.provision "artifactory", type: "ansible" do |ansible|
            ansible.inventory_path = "inventories/vagrant"
            #ansible.verbose = "v"
            ansible.limit = "master"
            ansible.playbook = "playbook.yml"
            ansible.become = true
            ansible.host_key_checking = false
        end
    end

end
