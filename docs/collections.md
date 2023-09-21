# Collections

How to use roles from the community and your own reusable roles for own projects.

## Community collections

- create a directory `collections` at the top level of your project
- add a file `requirements.yml` in the `collections` folder

Example:

```yml
---
# your playground - https://galaxy.ansible.com/
collections:
  - name: kubernetes.core
  - name: community.hrobot # for hetzner
  - name: community.general
  - name: ansible.posix
  - name: ansible.utils

# roles from your own git
roles:
  - name: my_modules
    src: https://github.com/egandro/ansible-modules
    version: main
    scm: git

```

Install the external collections/roles via:

```bash
ansible-galaxy install -r ./collections/requirements.yml --force
```

## Create your own roles via github

Idea from

- <https://blog.ruanbekker.com/blog/2022/04/19/publish-and-use-your-ansible-role-from-git/>

example:

```bash
ansible-playbook hello-git-roles.yaml
```
