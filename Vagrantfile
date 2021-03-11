
N = 3
Vagrant::configure("2") do |config|
    (0..N-1).each do |machine_id|
        config.vm.box = "centos/7"
        config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--audio", "none"]
        end
        config.vm.define "redis#{machine_id}" do |machine|
            machine.vm.hostname = "etcd#{machine_id}"
            machine.vm.network "private_network", ip: "192.168.60.#{10+machine_id}"
            if machine_id == N-1
                machine.vm.provision :ansible do |ansible|
                    ansible.galaxy_role_file = 'requirements.yml'
                    ansible.limit = "all"
                    ansible.playbook = "setup.yml"
                end
            end
        end
    end
end

