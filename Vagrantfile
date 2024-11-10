# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Seleccionar la imagen base
    config.vm.box = "ubuntu/jammy64" # Puedes elegir una versión de Ubuntu según prefieras
  
    # Configuración de hardware
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Provisionar la máquina e instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  
    # Reenvío de puertos (host: 8080, guest: 80)
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Compartir el directorio local con el de Apache en la máquina virtual
    config.vm.synced_folder "src", "/var/www/html", create: true
  end
  