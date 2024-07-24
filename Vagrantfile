Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y python3-pip python3-dev libpq-dev
    pip3 install virtualenv
    virtualenv venv
    source venv/bin/activate
    pip install -r /vagrant/app/requirements.txt
  SHELL

  config.vm.synced_folder ".", "/vagrant"

  config.vm.network "forwarded_port", guest: 5000, host: 5000
end