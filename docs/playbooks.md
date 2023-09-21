# Playbooks

- The script we execute.

## Inventory

- copy the `inventory/sample` to `inventory/my-hosts`
- edit `group_vars/all.yml` - adjust your ansible user

## Hello World

It is a yaml file

```yml
---
- name: sample book
  hosts: testvm
  vars:
       my_var: "something"

  tasks:
    - name: hello world
      ansible.builtin.debug:
        msg: Hello World {{ my_var }}
```

run

```bash
# preflight - syntax check
ansible-playbook -i inventory/sample/hosts.ini hello-world.yaml --syntax-check

# edit ansible.cfg to avoid the -i inventory ...
ansible-playbook hello-world.yaml
```

debug / log

```bash
ansible-playbook -vvv hello-world.yaml

# or via ansible.cfg
export ANSIBLE_LOG_PATH=/tmp/my-stuff
ansible-playbook -vvv hello-world.yaml
```

## Nginx

```bash
ansible-playbook install-nginx.yaml
curl http://testvm

ansible-playbook remove-nginx.yaml

# check the status if we run it again - there is no "changed"
ansible-playbook remove-nginx.yaml
curl http://testvm

```

