## ansible2-wl-patch
Stage and Prod Weblogic Patching


### Always verify  Patch Variables File [group_vars/all](https://githubg/ajitsingh25/ansible2-wl-patch/blob/master/group_vars/all)
```
view group_vars/all
```
#### Host Inventory Sample
```
[all]  
stage2cppxyz

[all:vars]  
ansible_python_interpreter=/x/opt/pp/bin/python  
ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
```

#### 1. [list_patch.yml](https://githubg/ajitsingh25/ansible2-wl-patch/blob/master/list_patch.yml)  List Patch
```
ansible-playbook -i inventory/stage/202 --ask-become-pass list_patch.yml -k
```

#### 2. [apply.yml](https://githubg/ajitsingh25/ansible2-wl-patch/blob/master/apply.yml)  Apply Patch
```
ansible-playbook -i inventory/stage/202 --ask-become-pass apply.yml -k --skip-tags debug
```

#### 3. [rollback.yml](https://githubg/ajitsingh25/ansible2-wl-patch/blob/master/rollback.yml) Rollback Patch
```
ansible-playbook -i inventory/stage/202 --ask-become-pass rollback.yml -k --skip-tags debug
```

#### 4. [restart_nm.yml](https://githubg/ajitsingh25/ansible2-wl-patch/blob/master/restart_nm.yml) Restart Node Manager
```
ansible-playbook -i inventory/stage/084 --ask-become-pass restart_nm.yml -k --skip-tags debug
```

#### 5. Working on hosts with logins "su - website"  
```
ansible-playbook -i inventory/live/su-host list_patch.yml --become-method=su --ask-become-pass -k
```
