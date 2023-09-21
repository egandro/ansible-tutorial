# Collections

How to use roles from the community for own projects.

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
```

example:

```bash
ansible-playbook hello-ansible-utils.yaml
```
