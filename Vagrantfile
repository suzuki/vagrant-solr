Vagrant.configure(2) do |config|
  config.ssh.forward_agent = true

  config.vm.box = "ubuntu/trusty64"
  config.vm.network 'forwarded_port', guest: 8983, host: 8983
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = "v"
    ansible.raw_ssh_args = ['-o ForwardAgent=yes -o ControlMaster=auto -o ControlPersist=1800s']
  end
end
