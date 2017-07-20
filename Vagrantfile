Vagrant.configure("2") do |config|

    ansible_inventory_dir = "/etc/ansible"
    #config.vm.box = "ubuntu/xenial64"

    config.vm.box = "bento/ubuntu-16.04"
    config.ssh.insert_key = false
#    config.vbguest.auto_update = true
    config.vm.box_check_update = true

    config.vm.define :"build" do |server|
        server.vm.network :private_network, ip: "172.20.30.10"
        server.vm.network "forwarded_port", guest: 80, host: 4321
        server.vm.provider :virtualbox do |v|
            v.name = "build"
            v.memory = "2048"
        end
    end

   #  config.vm.define :"dev" do |server|
   #     server.vm.network :private_network, ip: "172.20.30.11"
   #     server.vm.provider :virtualbox do |v|
   #         v.name = "dev"
   #         v.memory = "2048"
   #     end
   # end

    config.vm.provision :ansible do |ansible|
        ansible.playbook = "provision/main.yml"
       # ansible.inventory_path = "#{ansible_inventory_dir}/hosts"
        ansible.inventory_path = "/Users/alehbabkou/PycharmProjects/spg_igvm/provision/hosts"
        ansible.limit = 'all'
        ansible.sudo = true
    end

end