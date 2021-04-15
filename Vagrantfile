# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :vm1 do |vm1|
vm1.vm.box = "bento/centos-7.9"
vm1.vm.network :private_network, ip: "192.168.20.2"
vm1.vm.hostname = "vm1"
vm1.vm.provision "shell", path: "./scripts/server2.sh"
end
config.vm.define :firewall do |firewall|
firewall.vm.box = "bento/centos-7.9"
firewall.vm.network :"public_network", ip: "192.168.0.70"
firewall.vm.network "forwarded_port", guest: 80, host: 5081
firewall.vm.network "forwarded_port", guest: 443, host: 4569
firewall.vm.network :private_network, ip: "192.168.20.3"
firewall.vm.hostname = "firewall"
firewall.vm.provision "shell", path: "./scripts/server1.sh"

end
config.vm.define :vm2 do |vm2|
vm2.vm.box = "bento/centos-7.9"
vm2.vm.network :private_network, ip: "192.168.20.4"
vm2.vm.hostname = "vm2"
vm2.vm.network "forwarded_port", guest: 80, host: 5080
vm2.vm.network "forwarded_port", guest: 443, host: 4568
vm2.vm.provision "shell", path: "./scripts/server3.sh"
end
config.vm.define :vm0 do |vm0|
   vm0.vm.box = "bento/centos-7.9"
   vm0.vm.network :"public_network", ip: "192.168.0.90"
   vm0.vm.network "forwarded_port", guest: 80, host: 5082
   vm0.vm.network "forwarded_port", guest: 443, host: 4570
   vm0.vm.network :private_network, ip: "192.168.20.5"
   vm0.vm.hostname = "vm0"
   vm0.vm.provision "shell", path: "./scripts/server1.sh"
end
end

