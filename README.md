# What is Vagrant?

Vagrant is a tool for building and managing virtual machine environments in a single workflow focusing on automation. It lowers environment setup time, increases production parity, and makes the "works on my machine" excuse a relic of the past.

Vagrant is used to set up one or more virtual machines by:
1. Importing pre-made images called "boxes"
2. Initializing VM-specific settings such as IP addresses, hostnames, port forwarding, memory, etc.
3. Running provisioning software such as Ansible, Puppet, or Chef

Note that Vagrant doesn't install software or set up the machine past loading the VM and configuring initial settings. **Think of it as a scripting engine for virtual machines**.

While Vagrant ships out of the box with support for **VirtualBox**, **Hyper-V**, and **Docker**, Vagrant can also manage other types of machines using other **providers**.

Alternate providers can offer different features that make more sense in your use case. For example, if you use Vagrant for any real work, **VMware providers** are recommended since they're well supported and generally more stable and performant than VirtualBox.

## What does this demonstration do?

1. Brings up one **Virtual Machine** locally: **Ubuntu 20.04 LTS**
2. Uses **Ansible** to:
   - Check for and apply any available OS updates
   - Install **GitLab Community Edition**
   - Create certificates using **Let's Encrypt**
   - Configure **NGINX** to use **HTTPS**

## Requirements

1. A **Terminal**:
   - Windows users often choose one of the following: **Git-Bash** or **Cygwin** 
   - Apple users already have a terminal somewhere
   - Linux users already have a terminal somewhere
2. **Vagrant** and **VirtualBox** must already be installed
3. Add **192.168.56.10    gitlab.local** to your OS hosts file

## Deploy the demo

```bash
$ git clone git@github.com:lastofthedinosaurs/vagrant-ansible-gitlab.git
$ cd vagrant-ansible-gitlab
$ vagrant up
```

Typing `vagrant` from the command line will display a list of all available commands.

Be sure that you are in the same directory as the **Vagrantfile** when running these commands!

Use ` Vagrant destroy` in the same directory to stop and delete all traces of the demo when finished.
