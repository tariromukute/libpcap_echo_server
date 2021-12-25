# libpcap_echo_server
A simple echo vnf

The lifecycle management are defined in  ETSI GS NFV-IFA 007. The events are implemented in the `ansible/events` folder

## Install collection

The VNF uses a collection of ansible roles to set up the environment.

`ansible-galaxy install -r ansible/requirements.yml`

## Create inventory

This can be a server or a local VM on your machine

1. Generate ssh key to use to run ansible without password.
   
```bash
ssh-keygen

# Copy the public key to the machine
cat ~/.ssh/local_rsa.pub | ssh ovsxdp@192.168.122.155 "mkdir ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

2. Create inventory
   
```
[server]
server1 ansible_host=192.168.122.185 ansible_user=olan ansible_ssh_private_key_file=~/.ssh/local_rsa
```

## Test with molecule

You can run the test using molecule

```bash
cd ansible

molecule test
```

If you want to do some debug

```bash
cd ansible

# Run the tasks defined in molecule/converge
molecule converge

# ssh into the container
molecule login

# print the logs of the service
journalctl -o json-pretty -u olan-libpcap-echo-server
```