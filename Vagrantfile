# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"
  config.vm.network :forwarded_port, guest: 9000, host: 9000

  config.vm.synced_folder "srv/", "/srv/"

  config.vm.provision :salt do |salt|
    salt.minion_config = "srv/minion"
    # salt.bootstrap_script = "./install_salt.sh"
    salt.verbose = true
    salt.run_highstate = true
    salt.bootstrap_options = "-F -c /tmp -C -D"
  end

  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end
