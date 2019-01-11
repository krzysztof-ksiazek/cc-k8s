Vagrant.configure(2) do |config|

    config.ssh.insert_key = false

    config.vm.define "docker0" do |docker0|
        docker0.vm.box = "bento/ubuntu-16.04"
        docker0.vm.network "public_network", ip: "10.0.0.231", bridge: 'en0: Wi-Fi (Wireless)'
        docker0.vm.provider "virtualbox" do |vb|
            vb.memory = "4096"
            vb.cpus = 2

        end
    end

    config.vm.define "docker1" do |docker1|
        docker1.vm.box = "bento/ubuntu-16.04"
        docker1.vm.network "public_network", ip: "10.0.0.232", bridge: 'en0: Wi-Fi (Wireless)'
        docker1.vm.provider "virtualbox" do |vb|
            vb.memory = "4096"
            vb.cpus = 2

        end
    end

    config.vm.define "docker2" do |docker2|
        docker2.vm.box = "bento/ubuntu-16.04"
        docker2.vm.network "public_network", ip: "10.0.0.233", bridge: 'en0: Wi-Fi (Wireless)'
        docker2.vm.provider "virtualbox" do |vb|
            vb.memory = "4096"
            vb.cpus = 2

        end
        docker2.vm.provision "ansible" do |ansible|
            ansible.playbook="playbook.yml"
            ansible.groups = {
                "docker" => ["docker0", "docker1", "docker2"]
            }
            ansible.limit = 'docker'
        end
    end
end
