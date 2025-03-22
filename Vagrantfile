Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64" # Ubuntu 18.04 LTS
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end
  config.vm.synced_folder "./web", "/var/www/html"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    echo "<h1>Hola Mundo desde Apache en Vagrant</h1>" | sudo tee /var/www/html/index.html
    sudo systemctl restart apache2
  SHELL
end
