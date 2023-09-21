# Roles

Roles are a bunch of tasks that helps organize tasks.

## Let's create our own my-nginx role

- install nginx
- create a nice custom html page from a template including the name from a variable
- start nginx

Docs [here](https://galaxy.ansible.com/docs/contributing/creating_role.html).

```bash
ansible-galaxy --init-path roles  my-nginx
```

### Tour of the files we have

```txt
./README.md                 # add some meaningful here
./tasks/main.yml            # this is the top level task file - you need this
./defaults/main.yml         # put here default values that you want the user to change

# advanced things in the other files
./handlers/main.yml
./meta/main.yml
./tests/inventory
./tests/test.yml
./vars/main.yml             # this are variables that you usually don't want the user to be changing
```

### my-nginx example

```bash
ansible-playbook install-mynginx-role.yaml
curl http://testvm

# this is not perfect! /var/www/html is not cleaned
ansible-playbook remove-nginx.yaml
```

