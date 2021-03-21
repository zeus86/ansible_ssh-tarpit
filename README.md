# ansible_ssh-tarpit
Simple Ansible role and sample playbook to deploy a ssh-tarpit-node (https://github.com/Snawoot/ssh-tarpit). Ssh-tarpit is a  python3-implementation of a ssh-server, which sends data to clients slowly and endlessly, primarily to trap bots.

Most things are self explanatory, adjust the daemon-opts according to your needs in `roles/ssh-tarpit/default/main.yml` and the host in the example playbook. 

## Options:
`tarpit_port` Port to listen on  
`tarpit_ip` IP to bind to  
`tarpit_log` logfile location.  
`tarpit_interval`	Interval in seconds between every chunk of information to the client  
`tarpit_loglevel` info contains the connection attemtps (debug,info,warn,error,fatal)  
`tarpit_daemon_opts` crafted startup command  

## Limitations:
ssh-tarpit currently does not understand the Signal `HUP`, so on logrotate the Service gets restarted and trapped clients in this moment are getting released. This can be avoided, if you do not use logrotate, and use journalctl exclusively (see https://github.com/Snawoot/ssh-tarpit/issues/4)

## Compatibility:
Testet against Ubuntu 20.04 (yes, I know this will most likely not run on any distribution, maybe you need to tweak the installation of PIP3 beforehand).


