# ansible_ssh-tarpit
Simple Ansible role and sample playbook to deploy a ssh-tarpit-node (https://github.com/Snawoot/ssh-tarpit)

Most things are self explanatory, adjust the daemon-opts according to your needs in `roles/ssh-tarpit/default/main.yml` and the host in the example playbook. 

## Options explained:
`tarpit_port: 2200` Port to listen on  
`tarpit_ip: "{{ ansible_all_ipv4_addresses | first }}"` IP to bind to  
`tarpit_log: "/var/log/ssh-tarpit.log"` logfile location.  
`tarpit_interval: "2"`	Interval in seconds between every chunk of information to the client  
`tarpit_loglevel: "info"` info contains the connection attemtps (debug,info,warn,crit,fatal)  
`tarpit_daemon_opts: " -i {{ tarpit_interval }} -v {{ tarpit_loglevel }} -a {{ tarpit_ip }} -p {{ tarpit_port }} -f {{ tarpit_log }}"` crafted startup command  

## Limitations:
ssh-tarpit currently does not understand the Signal `HUP`, so on logrotate the Service gets restarted and trapped clients in this moment are getting released. This can be avoided, if you do not use logrotate, and use journalctl exclusively (see https://github.com/Snawoot/ssh-tarpit/issues/4)

## Compatibility:
Testet against Ubuntu 20.04 (yes, I know this will most likely not run on any distribution, maybe you need to tweak the installation of PIP3 beforehand).


