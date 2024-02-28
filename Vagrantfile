Vagrant.configure("2") do |config|
    # Указываем ОС, версию, количество ядер и ОЗУ
    config.vm.box = "centos/7"
 
    config.vm.provider :virtualbox do |v|
      v.memory = 4096
      v.cpus = 2
    end
  
    # Указываем имена хостов и их IP-адреса
    boxes = [
      { :name => "master",
        :ip => "192.168.11.150",
      },
      { :name => "slave",
        :ip => "192.168.11.151",
      }
    ]
    # Цикл запуска виртуальных машин
    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.network "private_network", ip: opts[:ip]
      end
      config.vm.provision "ansible" do |ansible|
         ansible.verbose = "vvv"
         ansible.playbook = "playbook.yml"
         ansible.become = "true"
   end
  end
  end
