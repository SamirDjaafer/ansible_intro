# Intro to ansible
##The first section for this guide in exclusive to MacOS. All other sections are standardized for usage in Ubuntu based Virtual Machines. 

### Setup for ansible on MacOS

1. Install ansible using homebrew. `brew install ansible`
2. Check if ansible installed correctly using `ansible --version`. You should be returned some ansible meta data. 

### Lets create a Vagrantfile

3. Ok now lets set up a Virtual Machine using Vagrant `Vagrant init ubuntu/xenial64`
4. Next we are going to add a VM for our Ansible machine called client. Add `config.vm.define "client" do |client|
    client.vm.hostname = "client"
end` to the `Vagrantfile`

### Installing ansible on our client VM

1. `Vagrant ssh` You should find yourself within `Vagrant@client`
2. Install the necessary repository with the command `sudo apt-add-repository ppa:ansible/ansible`
3. Update apt with the command `sudo apt-get update`
4. Install Ansible with the command `sudo apt-get install ansible -y`
5. Lastly ensure you have python installed as ansible requires a python interpreter `sudo apt-get install python -y`

- At this point ansible is installed and ready to go.
- Lets type in `ansible --version` and we should get some output.

### Adding our server VM

1. Lets go to our Vagrantfile
2. Underneath the previous VM we defined, lets define another one called server. `config.vm.define "server" do |server|
    sever.vm.hostname = "server"
end`
3. Lets run `vagrant up` to get our second VM up and running
4. We can check the status of our Virtual Machines using `vagrant status`
5. We should see both the `client` and `server` VM's running

### Adding a private network to our VM's

1. Lets go back to the vagrant file and configure a private network for our client and server VM's
2. `client.vm.network "private_network", ip: "192.168.33.10"` and `server.vm.network "private_network", ip: "192.168.33.20"`
3. As you can see we have given the two private networks different ip addresses.



