# User Collections

User Collections are [collections](collections.md) you create as library for your own projects.

## Installation (similar to the collections)

- create a directory `collections` at the top level of your project
- add a file `requirements.yml` in the `collections` folder

Example:

[Reference](https://docs.ansible.com/ansible/latest/dev_guide/developing_collections_creating.html)

```yml
---
collections:
# sample for user collection (bunch of roles you create to reuse)
  - name: https://github.com/egandro/ansible-tutorial-collection.git
    type: git
    version: main
```

Install the requirements:

```bash
ansible-galaxy install -r ./collections/requirements.yml --force
```

Sample playbook using a galaxy collection

```bash
ansible-playbook hello-ansible-user-collection.yaml
```
