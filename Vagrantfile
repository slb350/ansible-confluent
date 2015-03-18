# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
echo I am provisioning...
date > /etc/vagrant_provisioned_at
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
  config.ssh.forward_agent = true
end

Vagrant::Config.run do |config|

  config.vm.box = "casska.box"
  config.vm.box_url = "https://s3-us-west-1.amazonaws.com/sparkcentral-devopsna/casska.box"
  config.ssh.forward_agent = true

  config.vm.provision "ansible" do |ansible|
  ansible.playbook = "roles/tasks/install.yml"
  end
  
  config.vm.forward_port 2181, 22181
  config.vm.forward_port 9092, 29092
end
