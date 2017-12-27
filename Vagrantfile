# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # We're going to use CentOS 6.6 as required
    config.vm.box = "bento/centos-6.6"
    config.vm.box_version = "2.1.0"
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
      end

    N = 2
    (1..N).each do |i|
        config.vm.define "couchbase-#{i}" do |config|
          config.vm.hostname = "couchbase-#{i}"
          # Some assumptions has been made. We're going to connect our VM's
          # directly to our network using a network bridge
          # Keep in mind that if you have multiple interfaces in your physical
          # host, you'll be prompted to choose a suitable interface.
          config.vm.network "public_network"
          if i == N
            config.vm.provision :ansible do |ansible|
                # We're going to disable ansible default limit in order to
                # connect to all machines at the same time
                ansible.limit = "all"
                ansible.playbook = "playbook.yml"
                ansible.groups = {
                    "master" => ["couchbase-1"],
                    "slave" =>  ["couchbase-2"],
                }
                end
            end
        end
    end
end