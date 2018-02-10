
Vagrant.configure("2") do |config|

  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  #####################################################
  # You probably don't want to modify below this line #
  #####################################################
  
  config.vm.box = "jcbbjjttt/cityscroller"
  config.vm.synced_folder "./src", "/var/www/html"  
  
  config.ssh.insert_key = false
  config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |vb|

    # Customize the amount of memory on the VM:
    vb.memory = "1532"
    vb.name = "cityscroller"
  end

  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get upgrade -y
     while [ $? -ne 0 ]; do
       sleep 1
       apt-get upgrade -y
     done

     ln -s /var/www/html/cityScroller.js /var/www/html/cityScroller.pde

   SHELL
  
end
