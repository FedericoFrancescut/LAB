# -*- mode: ruby -*-

# vi: set ft=ruby :

 

hosts = [

  { :hostname => "n1-k8s-controlplane",  :ip => "192.168.77.10", :cpu => "2", :ram => "2048" },

  { :hostname => "n2-k8s-worker1",  :ip => "192.168.77.11", :cpu => "2", :ram => "2048" },

  { :hostname => "n3-k8s-worker2",  :ip => "192.168.7712", :cpu => "2", :ram => "2048" },

  { :hostname => "n4-k8s-bastion",  :ip => "192.168.77.13", :cpu => "2", :ram => "2048" },

]

 

Vagrant.configure("2") do |config|

  # always use Vagrants insecure key

  config.ssh.insert_key = false

  # forward ssh agent to easily ssh into the different machines

  config.ssh.forward_agent = true

  check_guest_additions = true

  functional_vboxsf = false

  config.vm.box = "bento/ubuntu-20.10"

  hosts.each do |host|

    config.vm.hostname = host[:hostname]

    config.vm.define host[:hostname] do |machine|

      machine.vm.network "private_network", ip: host[:ip]

      machine.vm.provider "virtualbox" do |v|

        v.name = host[:hostname]

        v.cpus = host[:cpu]

        v.memory = host[:ram]

      end

    end

  end

end