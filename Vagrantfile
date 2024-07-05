Vagrant.configure("2") do |config|
    # Configuración de la primera máquina virtual
    config.vm.boot_timeout = 600 # Tiempo en segundos (10 minutos)
    config.vm.define "web1" do |web1|
      web1.vm.box = "ubuntu/bionic64"
      web1.vm.network "private_network", ip: "192.168.33.10"
      web1.vm.synced_folder "./html", "/var/www/html"
      web1.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl enable apache2
        sudo systemctl start apache2
      SHELL
    end
  
    # Configuración de la segunda máquina virtual
    config.vm.define "web2" do |web2|
      config.vm.boot_timeout = 600 # Tiempo en segundos (10 minutos)

      web2.vm.box = "ubuntu/bionic64"
      web2.vm.network "private_network", ip: "192.168.33.11"
      web2.vm.synced_folder "./html", "/var/www/html"
      web2.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl enable apache2
        sudo systemctl start apache2
      SHELL
    end
  end
  