# base
base role for managing users, groups and packages

## Requirements
* ansible 2.8+
* molecule 3.6+

## Example
```
base_groups:
  - name: sudo-no-pass
    state: present
    sudoers: true
    no_passwd: true
  - name: sudo
    state: present
    sudoers: true
    no_passwd: false
  - name: wheel
    state: present
    sudoers: false
  - name: docker
    state: present
    sudoers: false
    system: yes

base_users:
  - name: roman_starik
    groups:
      - sudo-no-pass
      - docker
    key_path: '~/.ssh/id_rsa.pub'

base_packages:
  main:
    - neovim
    - tmux
    - jq
```

## Tests
just run `molecule test`
