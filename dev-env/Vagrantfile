# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define :alpha do |alpha|
    alpha.vm.box = "centos/7"
    alpha.vm.hostname = "alpha"
    alpha.vm.provision "shell", inline: <<-SHELL
	sudo curl -s -O https://raw.githubusercontent.com/perfsonar/pscheduler/master/scripts/system-prep
	sudo sh ./system-prep
	sudo yum install git
	git clone https://github.com/perfsonar/pscheduler.git
	cd pscheduler
        sudo make
    SHELL
  end
  config.vm.define :gamma do |gamma|
    gamma.vm.box = "centos/7"
    gamma.vm.hostname = "gamma"
    gamma.vm.provision "shell", inline: <<-SHELL
        sudo curl -s -O https://raw.githubusercontent.com/perfsonar/pscheduler/master/scripts/system-prep
        sudo sh ./system-prep
        sudo yum install git
        git clone https://github.com/perfsonar/pscheduler.git
        cd pscheduler
        sudo make
    SHELL
  end

  config.vm.define :beta do |beta|
    beta.vm.box = "centos/7"
    beta.vm.hostname = "beta"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--audio", "none"]
  end
end
