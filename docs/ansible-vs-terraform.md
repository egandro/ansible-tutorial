# Ansible vs. Terraform

- you can do the same!

but..

## Ansible

- feels more like a batch job
  - we start it
  - it modifies the OS
  - (maybe with some conditions / variables)
  - it's done
  - no state tracked
- no easy undo - unless you write an undo batch job
- ansible is smart
  - e.g. "I want nginx installed and running"
  - it won't run `apt-get install` twice

## Terraform

- it feels more like controlling a ship "I want to go now x... Now I want to go y"
- run 1:
  - install a new node with ip 1
  - install software xyz
  - the state is tracked
- run 2:
  - edit the script or parameters and
  - add ip 2
  - remove software xyz
- Terraform get tiny input files and the provider has `magic sauce` to plan what todo and what to apply.

## Boths

- handle variables, array/structures/yaml/json of variables, secrets
- tons of libraries
- create your own module
- create your own module in a low level language
  - Python
  - C
  - Go
  - ...

## When to use what?

- Depends on your situation / what is there
- Terraform is limited by the provider you get.
- Ansible only needs ssh (nothing preinstalled).
