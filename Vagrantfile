
Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/xenial64"
    config.vm.network "private_network", ip: "192.11.11.11"

    config.vm.provision "shell", inline: <<-SHELL

        debconf-set-selections <<< 'mysql-server mysql-server/root_password password root'
        debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password root'
        apt-get update
        apt-get install -y php7.0 apache2 libapache2-mod-php7.0 mysql-server

        mysql -uroot -proot -e "create database tutor"

        echo 'cd /vagrant' >> /home/vagrant/.bashrc
    SHELL
end
