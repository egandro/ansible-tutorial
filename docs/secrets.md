# Secrets

Ansible has a built in support for secrets.

You can even commit them to git - but should you?

## Create a secret file

```bash
ansible-vault create secrets.enc
# enter a secure password
```

Vi / Nano etc. starts - now create your yaml file.

```yml
# foo is now just a regular variable
foo: bar
```

content of the file

```bash
cat secrets.enc
$ANSIBLE_VAULT;1.1;AES256
32343664633934616539633530616632396532326364366332633732303031663161303333623130
6139386364366334316632326164373833626661323465660a633837633639666232386463396436
64646630633961626531393834643937393365316536653231643564383564666162386161346230
6633323966313530390a346438663065316232666662326363636463666133663835316335383631
6166
```

edit the file again with

```bash
ansible-vault edit secrets.enc
```

## How to use the secret file?

### bad version - but that is how the documentation tells us to do it

```bash
echo -n "mysecret"  > vault.pwd
ansible-playbook sample.yaml --vault-password-file vault.pwd -e @secrets.enc
```

### nice (but not documented) version

```bash
export ANSIBLE_VAULT_PASSWORD=mysecret
echo -n "${ANSIBLE_VAULT_PASSWORD}" | ansible-playbook sample.yaml -e @secrets.enc --vault-password-file=/bin/cat
```




