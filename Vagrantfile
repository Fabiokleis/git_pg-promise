# -*- mode: ruby -*-
# vi: set ft=ruby  :

# setup 3 machines with this stats
machines = {
  "ansible"=> {"memory" => "1024", "cpu" => "1", "ip" => "30", "image" => "centos/7"},
  "debian" => {"memory" => "512",  "cpu" => "1", "ip" => "31", "image" => "debian/buster64"},
  "ubuntu" => {"memory" => "512",  "cpu" => "1", "ip" => "32", "image" => "ubuntu/bionic64"}
}

Vagrant.configure("2") do |config|
  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.sysadmin.example"
      machine.vm.network "public_network", ip: "192.168.1.#{conf["ip"]}", bridge: "enp3s0f0"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
        vb.customize ["modifyvm", :id, "--groups", "/iac"]
      end
    config.vm.provision "shell", inline: <<-EOF
      echo '192.168.1.30 ansible.sysadmin.example' >> /etc/hosts
      echo '192.168.1.31 debian.sysadmin.example' >> /etc/hosts
      echo '192.168.1.32 ubuntu.sysadmin.example' >> /etc/hosts
      EOF
    end
  end
end
