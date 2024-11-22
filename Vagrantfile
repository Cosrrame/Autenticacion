# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/bookworm64"

  config.vm.define "mrm" do |mrm|
  mrm.vm.network "private_network", ip: "192.168.57.10"

  mrm.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt install -y git
    sudo apt install -y nginx

#Primera web (perfectLearn)

    sudo mkdir -p /var/www/mrm/html
    git clone https://github.com/cloudacademy/static-website-example /var/www/mrm/html
    sudo chown -R www-data:www-data /var/www/mrm/html
    sudo chmod -R 755 /var/www/mrm

    sudo cp /vagrant/files/mrm /etc/nginx/sites-available/mrm

    sudo ln -sf /etc/nginx/sites-available/mrm /etc/nginx/sites-enabled/
    sudo nginx -t
    sudo systemctl restart nginx

#Segunda web (perfectLearn)

    sudo mkdir -p /var/www/perfectLearn/
    sudo cp -r /vagrant/files/html /var/www/perfectLearn/
    sudo chown -R www-data:www-data /var/www/perfectLearn/html
    sudo chmod -R 755 /var/www/perfectLearn

    sudo cp /vagrant/files/perfectLearn /etc/nginx/sites-available/perfectLearn

    sudo ln -sf /etc/nginx/sites-available/perfectLearn /etc/nginx/sites-enabled/
    sudo nginx -t
    sudo systemctl restart nginx


    sudo sh -c "echo -n 'marcos:' >> /etc/nginx/.htpasswd"
    sudo sh -c "openssl passwd -apr1 '1234' >> /etc/nginx/.htpasswd"
    sudo sh -c "echo -n 'ramos:' >> /etc/nginx/.htpasswd"
    sudo sh -c "openssl passwd -apr1 '1234' >> /etc/nginx/.htpasswd"
    
    sudo cat /etc/nginx/.htpasswd
    
  SHELL
  end 
end