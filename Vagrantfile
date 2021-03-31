Vagrant.configure('2') do |config|
    servers=[
      {
        :name => 'dev1',
        :hostname => 'dev1.darthlore.dvnet',
        :box => 'centos7',
        :ip => '192.168.56.120',
        :ssh_port => '2210'
      },
      {
        :name => 'web1',
        :hostname => 'web1.darthlore.dvnet',
        :box => 'rhel7.4-bestinet',
        :ip => '192.168.56.121',
        :ssh_port => '2211'
      },
      {
        :name => 'db1',
        :hostname => 'db1.darthlore.dvnet',
        :box => 'rhel7.4-bestinet',
        :ip => '192.168.56.122',
        :ssh_port => '2212'
      }
  
  ]
  
  servers.each do |machine|
    
    config.vm.define machine[:name] do |node|
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
  
      node.vm.network :private_network, ip: machine[:ip]
      node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
  
      node.vm.provider :virtualbox do |v|
        v.customize ['modifyvm', :id, '--memory', 512]
        v.customize ['modifyvm', :id, '--name', machine[:name]]
      end
    end
  end
  
  config.ssh.insert_key = false
  
  end