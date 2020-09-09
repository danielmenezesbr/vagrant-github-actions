# -*- mode: ruby -*-
# vi: set ft=ruby :
$domain = "mshome.net"
$domain_ip_address = "192.168.56.2"
$ubuntu_ip_address = "192.168.56.14"

unless Vagrant.has_plugin?("vagrant-vbguest")
  puts 'Installing vagrant-vbguest Plugin...'
  system('vagrant plugin install vagrant-vbguest')
end

unless Vagrant.has_plugin?("vagrant-reload")
  puts 'Installing vagrant-reload Plugin...'
  system('vagrant plugin install vagrant-reload')
end

Vagrant.configure("2") do |config|

  config.vm.define "dc" do |config|
    config.vm.box = "cdaf/WindowsServerDC"
    config.vm.box_version = "2020.05.14"
	  

    config.winrm.username = "vagrant"
    config.winrm.password = "vagrant"
    config.vm.guest = :windows
    config.vm.communicator = "winrm"
    config.winrm.timeout = 2800 # 30 minutes
    config.winrm.max_tries = 40
    config.winrm.retry_limit = 200
    config.winrm.retry_delay = 10
    config.vm.graceful_halt_timeout = 600

    config.vm.hostname = "winserver"
    config.vm.network "private_network", ip: "192.168.56.2"

    config.vm.provider :virtualbox do |v, override|
      v.memory = 2024
	    v.cpus = 1
	    v.gui = false
    end

    config.vbguest.auto_update = false
  end

  config.vm.box_check_update = false
  config.vm.boot_timeout = 2800

end
