Vagrant.configure("2") do |config|
  config.vm.box = "matthiasmullie/debian9-arm64"
  config.vm.box_version = "1.0.0"
  config.vm.synced_folder "For_Vagrant", "/home/vagrant/www/default/", type: "rsync"
  
  config.vm.network "forwarded_port", guest: 80, host: 1234, host_ip: "127.0.0.1"
  
  config.vm.provision "shell", inline: <<-SHELL
   apt-get -y update
   apt-get -y upgrade
   apt-get -y install nginx
   cp /home/vagrant/www/default/file.html /var/www/html/index.nginx-debian.html
   chmod 755 /home/vagrant
   service nginx restart
   SHELL
end
