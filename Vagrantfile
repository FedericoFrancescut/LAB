# -*- mode: ruby -*-

# vi: set ft=ruby :

 

hosts = [

  { :hostname => "n0-k8s-bastion",        :ip => "192.168.1.110", :cpu => "1", :ram => "1024" },

  { :hostname => "n1-k8s-controlplane1",  :ip => "192.168.1.111", :cpu => "2", :ram => "1792" },

  { :hostname => "n2-k8s-controlplane2",  :ip => "192.168.1.112", :cpu => "2", :ram => "1792" },

  { :hostname => "n3-k8s-controlplane3",  :ip => "192.168.1.113", :cpu => "2", :ram => "1792" },

# { :hostname => "n4-k8s-infraworker1",   :ip => "192.168.1.114", :cpu => "1", :ram => "1280" },

# { :hostname => "n5-k8s-infraworker2",   :ip => "192.168.1.115", :cpu => "1", :ram => "1280" },

# { :hostname => "n6-k8s-infraworker3",   :ip => "192.168.1.116", :cpu => "1", :ram => "1280" }

# { :hostname => "n7-k8s-computeworker1", :ip => "192.168.1.117", :cpu => "2", :ram => "1536" },

  { :hostname => "n8-k8s-computeworker2", :ip => "192.168.1.118", :cpu => "2", :ram => "1536" },

  { :hostname => "n9-k8s-computeworker3", :ip => "192.168.1.119", :cpu => "2", :ram => "1536" }

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