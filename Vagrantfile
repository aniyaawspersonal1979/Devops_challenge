Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|

  config.vm.box = "gbarbieru/xenial"
  unless Vagrant::DEFAULT_SERVER_URL.frozen?
    Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')
  end
  config.vm.provider :virtualbox do |vb|
    vb.gui = true
  end

  config.vm.network "private_network", ip: "10.10.10.20"

  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "site.yml"
  end
  config.vm.provider :virtualbox do |vb|
    cpus = `nproc`.to_i
    vb.customize ["modifyvm", :id, "--cpus", cpus]
  end

end
