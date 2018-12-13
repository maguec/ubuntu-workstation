#n -*- mode: ruby -*-
# vi: set ft=ruby :
#

Vagrant.configure("2") do |config|

# Bootstrap for Ansible
  config.vm.provision "shell",
    inline: "sudo apt-get update && DEBIAN_FRONTEND=noninteractive sudo apt-get -y install python"

  config.vm.box         = "ubuntu/xenial64"
  config.vm.hostname    = "workstation"

  config.vm.provider "virtualbox" do |v|
    v.customize  ["modifyvm", :id, "--audio", "none"]
  end


  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "tests/vagrant.yml"
    ansible.extra_vars = {
      gui_install: "False",
      vim_plugin_install: "False",
      ubuntu_user: "vagrant"
    }
    ansible.become   = "true"
    ansible.verbose  = "true"
  end

end

