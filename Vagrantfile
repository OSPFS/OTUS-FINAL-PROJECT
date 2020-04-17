
MACHINES = {
    :isp => {
          :box_name => "centos/7",
          :public => {ip: '10.0.1.201', adapter: 2, netmask: "255.255.255.0", bridge: "en0: Ethernet", auto_config: false},
          :net =>  [ 
                     {ip: '10.10.1.1', adapter: 3, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},
                   ]
    },
    :router1 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.1.2', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},
                     {ip: '10.10.10.2', adapter: 3, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},
                  ]
    },
    :router2 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.1.3', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},
                     {ip: '10.10.10.3', adapter: 3, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},
                  ]
    },
    :balancer => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.10.10', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
                  ]
    },
    :webapp1 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.10.11', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
                  ]
    },
    :webapp2 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.10.12', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
                  ]
    },
    # :dbproxy => {
    #       :box_name => "centos/7",
    #       :net => [
    #                  {ip: '10.10.10.13', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
    #               ]
    # },
    :db1 => {
          :box_name => "centos/7",
          :net => [
                     {ip: '10.10.10.14', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
                  ]
    },
    # :db2 => {
    #       :box_name => "centos/7",
    #       :net => [
    #                  {ip: '10.10.10.15', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
    #               ]
    # },
    # :db3 => {
    #       :box_name => "centos/7",
    #       :net => [
    #                  {ip: '10.10.10.16', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "lab-net", auto_config: false},                     
    #               ]
    # },
}
  
  Vagrant.configure("2") do |config|
  
    MACHINES.each do |boxname, boxconfig|
  
      config.vm.define boxname do |box|
  
          box.vm.box = boxconfig[:box_name]
          box.vm.host_name = boxname.to_s
  
          boxconfig[:net].each do |ipconf|
            box.vm.network "private_network", ipconf
          end
          
          if boxconfig.key?(:public)
            box.vm.network "public_network", boxconfig[:public]
          end
          
          box.vm.provider "virtualbox" do |v|
           v.memory = 1024
           v.cpus = 2
          end
            
        end

    end
    
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.compatibility_mode = "auto"
      ansible.become = "true"
    end

  end
