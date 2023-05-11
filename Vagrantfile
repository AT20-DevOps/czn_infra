$script = <<-SCRIPT
cd ConverterService
docker-compose up
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  # Configure provisioners on tha machine
  config.vm.provision :docker
  config.vm.provision :docker_compose
  

  # Server 1
  config.vm.define "ci-server" do |ciserver|
    ciserver.vm.network "private_network", ip: '192.168.56.60'
    ciserver.vm.hostname = "ci-server"
  end

  # Server 2
  config.vm.define "server-2" do |server2|
    server2.vm.network "private_network", ip: '192.168.56.61'
    server2.vm.hostname = "server2"
    config.vm.provision :file, source: "AT20_CONVERT_SERVICE", destination: "ConverterService"
    server2.vm.provision "shell", inline: $script
  end
end
