# Collections

Collections = Roles of the community for a specific topic e.g. Kubernetes.

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

Install the requirements:

```bash
ansible-galaxy install -r ./collections/requirements.yml --force
```

Sample playbook using a galaxy collection

```bash
ansible-playbook hello-ansible-utils.yaml
```
