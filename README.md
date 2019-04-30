# K3s Testing Playbook
Playbook and vagrant file to deploy k3s in testing environments.

WARNING: Because I use this as a testing base, there will be roles added and removed to place helm charts to deploy services for me to test. I'm not really branching this, so HEAD will always be a moving target. If you want to adapt this to your own use, please fork and modify as needed. I probably won't accept PRs to this unless it directly relates to a project I am working on.

## How to use:
If you are testing k3s locally on your laptop or desktop computer, you need only clone this repository and issue the following command from inside the created directory: 

`vagrant up`

If you are using this playbook to install k3s on a group of hosts external to your workstation/laptop then you will need to fill out the hosts.ini and issue the following command:

`ansible-playbook -i hosts.ini site.yml`

Note: If using the second scenario, you may need to adjust to your environment as needed, such as providing sudo/become information or setting up SSH keys on the hosts you want to install on.

###Deploying a helm chart:

If you want to deploy a helm chart post-cluster creation, modify the task on line 11 in the helmchart role tasks/main.yml file. Make sure you place the template as similar to provided currently by the "anchore.yaml.j2" file.

As is currently, this project will deploy Anchore engine automatically.

## Requirements:

### Scenario 1: Local testing
- Ansible Version 2.7 or higher
- VirtualBox 5.2 or higher
- Vagrant 2.0 or higher
	- Vagrant-vbox plugin
- Laptop with at least 12G ram
- MacOS or Linux host operating system 

### Scenario 2: Installing k3s on VMs/computers on a network/in a cloud service

- Ansible Version 2.7 or higher
- SSH Keys exchanged or ssh user/password set in hosts.ini
- Debian 9 on target hosts, preferrably a minimal/headless install with no colocated services

## Notes:

### What it currently does:
- Install k3s on debian hosts and join them in a cluster
	- Either in a vagrant setup or on remote hosts
	- Can support arm (ie: Raspbian/Raspberry Pi cluster installs)

### To-Do list:
- Add RHEL/Cent support
- per https://github.com/rancher/k3s/issues/24 need to fix virtualbox NAT issues with node communication

## Don't Run With Scissors:

THE SOFTWARE IS PROVIDED ON AN "AS IS" BASIS, AND NO WARRANTY, EITHER EXPRESS OR IMPLIED, IS GIVEN. YOUR USE OF THE SOFTWARE IS AT YOUR SOLE RISK.