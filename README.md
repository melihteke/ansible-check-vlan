# Ansible Playbook for Checking a VLAN on Cisco Devices

This Ansible playbook checks if VLAN 2000 exists on Cisco devices and writes the result to a CSV file.

## Requirements

- Ansible
- Python
- Access to Cisco devices via SSH

## Variables

- `ansible_network_os`: The network operating system. This should be set to `ios` for Cisco devices.
- `vlan_exists`: A fact that is set to `true` if VLAN 2000 exists on the device, and `false` otherwise.

## Tasks

1. **Run 'show vlan' command**: This task runs the `show vlan` command on the Cisco device and registers the output in the `result` variable.

2. **Print 'show vlans' output**: This task prints the output of the `show vlan` command.

3. **Check if VLAN 2000 exists**: This task checks if VLAN 2000 exists in the output of the `show vlan` command.

4. **Write to CSV file**: This task writes the hostname of the device and whether VLAN 2000 exists to a CSV file. The file is created if it doesn't exist.

## Usage

## Clone Repo
```sh
git clone https://github.com/melihteke/ansible-check-vlan.git
```

## Vault
Sensitive data like device credentials are stored in an Ansible Vault file. The path to the vault file is /home/mteke/ansible/vault.yml. To edit the vault file, use the ansible-vault edit command.

### To create a new Vault 
```sh
[mteke@mac01 ansible]$ ansible-vault create new_vault.yml
New Vault password: 
Confirm New Vault password: 
[mteke@mac01 ansible]$ 
```

### To edit already existing Vault
```sh
[mteke1@mac01 ansible]$ ansible-vault edit new_vault.yml
Vault password: 
```

### Vault File Content
vault.yml
```sh
---
ansible_user: mteke
ansible_password: your_password
```
This is just a sample encrypted vault file. the content is already changed so. it can not be used anymore. I just left this here for visual representation.

![image](https://github.com/melihteke/ansible-check-vlan/assets/36086368/ad5012d9-d1ee-40c7-a348-92b27705e9ec)


## Run Playbook
To run the playbook, use the following command:
```bash
ansible-playbook -i hosts.ini check-vlan.yaml --ask-vault-pass
```
Replace **hosts.ini** with your inventory file and playbook.yml with the path to this playbook. The --ask-vault-pass option prompts for the vault password.




