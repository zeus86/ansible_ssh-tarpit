# ansible_ssh-tarpit
Simple Ansible Playbook to deploy a ssh-tarpit (https://github.com/Snawoot/ssh-tarpit)

Most things are self explanatory, adjust the daemon-opts according to your needs in `roles/ssh-tarpit/default/main.yml` and the host in the example playbook. Testet against Ubuntu 20.04 (yes, I know this will most likely not run on any distribution).
