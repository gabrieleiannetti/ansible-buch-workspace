# Workspace for ansible-Buch

A workspace for learning and practicing based on the book [ansible-buch](https://github.com/ansible-buch/ansible-buch) by Axel Miesen

## Starting the Hosts

-> Vagrant, see `Vagrantfile`

## Admin Host

-> ansible VM  

### Ansible Playbooks

#### copy\_file with File Decryption

```bash
vagrant@ansible:~/ansible/projects/start$ ansible-playbook --vault-id /home/vagrant/pw playbooks/copy_file.yml
```
