# ansible-primer
Quick workshop on Ansible for weekly tech sessions. Accompanying slides [here](https://docs.google.com/presentation/d/1ro7BsMg03a4S4NrrCjer2MjNi3vG4KCJfbyaBNadiTg/edit?usp=sharing)

### Prerequisites
* Access to a Linux/OSX box
* Virtualbox
* Ansible (2.x)

**Starting vanilla hosts for your lab set up**
1. Open a shell
2. Clone this repo
3. `cd ansible-primer/src`
4. Run `vagrant up` and wait for the machines to boot
5. Once all the boxes are up, you'll have three pristine nodes(192.168.20.10, 192.168.20.11 and 192.168.20.12) to play with.
6. Ping them one-by-one and see if all are responding. They should :)

Note: Initial download of Ubuntu bento box takes a while (to download about `1.8G` of data). You may tweak it to a lighter vagrant box image by modifying the `Vagrantfile`. A list of vagrant boxes is available [here](https://app.vagrantup.com/boxes/search).

**Establishing key based SSH login**  
Ansible uses SSH to login to remote hosts and execute configuration tasks. Before we can start playing around with Ansible, this one last set up step needs to be done as well.
1. Ensure you have ssh keypair set up on your control host(local box from where you run ansible). If not, generate a keypair by running `ssh-keygen` and follow on screen instructions. Truck loads of useful documentation on `ssh-keygen` can be found [here](https://www.ssh.com/ssh/keygen/)
2. `ssh-copy-id` is used to copy your identity (public key) to the remote host. In our Vagrant based lab set up, each box that has been provisioned by vagrant includes a user account, named `vagrant` with default password `vagrant`. From the control machine, run `ssh-copy-id vagrant@<target-node>`, to copy your id to the target nodes. 
3. Check if the keys are installed successfully, by running `ssh vagrant@<target-node>`. If the keys were installed successfully, you'll be able to login without password, but with key-based authentication

**First encounter with ansible**  
Now that you have set up SSH logins, let's run our first ansible command
1. From `ansible-primer/src/ansible`, run `ansible -i hosts -m ping all`
2. You should see an output similar to the below
````bash
control-host | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
database | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
webserver1 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
webserver2 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
````
