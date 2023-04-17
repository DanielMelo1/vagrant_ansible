
Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = "1"
  end
  
  
  config.vm.box = "ubuntu/focal64"
  config.vm.synced_folder "./ansible", "/ansible"
  config.vm.network "forwarded_port", guest: 80, host: 8090
  config.vm.network "public_network" 

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y ansible
    ansible-playbook  --connection=local /ansible/playbook.yml
  SHELL
end
