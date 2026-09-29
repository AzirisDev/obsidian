It way of being deterministic with changes and not be error-prone. It is used for automation in general. But it is also used for network automation.

It is made of many components:
- `Control pane` - one device is chosen to be the controlling one and which send in `push-based` manner sends via ssh connection the `Ansible modules`.
- `Ansible modules` - performs any task on the device  
- `Inventory` - yaml file that contains list of all devices. You can identify what machines do you have and how to group them
```
all:
  vars:
    ansible_user: azim
  children:
    webservers:
      hosts:
        web1: { ansible_host: 192.168.1.10 }
        web2: { ansible_host: 192.168.1.11 }
```
- `Templates` - config files with Jinja2 placeholders, rendered per host using your variables and facts. It is logic for applying configs to devices.
- `Playbook` - yaml file containing one or more **plays**. Each play maps a group of hosts to a list of **tasks**, and each task calls one module. It is idempotent - it changes only if necessary. 
- `Host vars` - yaml file with interfaces and IP addresses and names configured, that can be reused.

Links:

202609241238

