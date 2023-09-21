# Inventory

An [inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) contains information on the hosts that we want to run ansible.

Concept: Your Host -> Inventory -> 0, 1 or n hosts we want to run the file.

More nice docs [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-ansible-inventories).

## Inventory file

(We use the `ini` format. There is also a `yaml` format.)

Example 1.

```ini
[core]
localhost
```

Example 2.

```ini
[webservers]
webserver1
webserver2
pi-server4
10.13.4.1
www[01:50].example.com # your 50 servers...

[firewalls]
fw1
fw3
fw3
```

- We can now reference the hosts via `hosts: core` or `hosts: webservers` or `hosts: firewalls`.

## SSH Setup

- You need to setup ssh keys to jump into the machines.
  - Use a non privileged user e.g. `ansible`.
  - Allow the `ansible` user to run sudo without a password.
- However - you add all levels of [security](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_privilege_escalation.html). You can even use jump hosts etc.
- Ansible uses the term of `become` (an operation that needs sudo) and `become_user` the user we want to become. This is very often `root` but might also be `postgres` etc.
- sometimes it's expected that a host is down - then you need to use `ignore_unreachable: true` in your scripts.

## Test the inventory

```bash
ansible-inventory -i inventory --list
ansible all -i inventory -m ping # all is an alias for "all"
ansible webservers -i inventory -m ping
```

## Advanced concepts

Ansible can use variables (covered later...) - you can apply them on a host basis in the inventory.

Example (in `yaml`)

```yaml
super_computers:
  hosts:
    host1:
      http_port: 80 #  < variables per host
      maxRequestsPerChild: 808
    host2:
      http_port: 303
      maxRequestsPerChild: 909
```

Same in `ini`

```ini
[super_computers]
host1 http_port=80 maxRequestsPerChild=808
host2 http_port=303 maxRequestsPerChild=909
```

## Best practice

- Your "end user" - if this is not you in your basement - , needs two things.
  - a sample inventory
  - a base set of variables that are documented
- create a `inventory` directory at the top level:

```txt
inventory/.gitignore
inventory/sample/hosts.ini
inventory/sample/group_vars/proxmox.yml
inventory/sample/group_vars/all.yml
```

hosts.ini

```txt
[proxmox]
192.168.30.40

[firewalls]
192.168.10.1
192.168.10.2
192.168.10.3
```

The `group_vars` is a directory that ansible automatically queries. If you use `proxmox` or `firewalls` these variables are always applied to them. As always `all` will be used for all hosts.

Write nice documentation to your variables.
