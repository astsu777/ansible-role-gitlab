DEV_HOSTNAME = "gitlab-ce"
DEV_BOX = "ubuntu/focal64"
DEV_RAM = "4096"
DEV_IP = "192.168.56.10"

Vagrant.configure("2") do |config|

  config.vm.define DEV_HOSTNAME do |gitlab|
    gitlab.vm.box = DEV_BOX
    gitlab.vm.provider "virtualbox" do |vb|
      vb.memory = DEV_RAM
    end
    gitlab.vm.network "private_network", ip: DEV_IP
    gitlab.vm.hostname = DEV_HOSTNAME
    gitlab.vm.synced_folder "./provision", "/provision"
    gitlab.vm.provision "ansible_local" do |ansible|
      ansible.become = true
      ansible.playbook = "provision/gitlab-ce.yaml"
      ansible.galaxy_roles_path = "/etc/ansible/roles"
      ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
    end
  end

end
