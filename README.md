### Домашнее задание #11 (Ansible)
#### Установка Ansible
- Проверим актуальную версию Python:
```console
[kita@localhost ~]$ python -V
Python 2.7.5
```
- Установим Ansible, проверим версию:
```console
[kita@localhost ~]$ ansible --version
ansible 2.9.27
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/kita/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Jun 28 2022, 15:30:04) [GCC 4.8.5 20150623 (Red Hat 4.8.5-44)]
```
- создал каталог ansible, поместил vagrantfile в директорию, запустил виртуальную машину:
```console
[kita@localhost ~]$ ls -l /home/kita/OTUS/Otus_Unit_12_Ansible/
total 4
-rw-rw-r--. 1 kita kita 847 Oct  1 08:43 Vagrantfile
[kita@localhost ~]$


[kita@localhost Otus_Unit_12_Ansible]$ vagrant ssh-config
Host nginx
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /home/kita/OTUS/Otus_Unit_12_Ansible/.vagrant/machines/nginx/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```
- создал файл hosts в директории ansible/inventory, настроил параметры, проверил доступность управляемого клиента:
```console
[kita@localhost Otus_Unit_12_Ansible]$ cat inventory/hosts
[web]
nginx ansible_host=127.0.0.1 ansible_port=2222 ansible_user=vagrant ansible_private_key_file=/home/kita/OTUS/Otus_Unit_12_Ansible/.vagrant/machines/nginx/virtualbox/private_key


[kita@localhost Otus_Unit_12_Ansible]$ ansible nginx -i inventory/hosts -m ping
The authenticity of host '[127.0.0.1]:2222 ([127.0.0.1]:2222)' can't be established.
ECDSA key fingerprint is SHA256:+Vo+cqNTADEFQ7o/Wt4z7fJLdzkQG6Ny+efJj0Dp4D4.
ECDSA key fingerprint is MD5:9f:1a:c4:4b:98:d7:02:83:6d:f4:0e:93:86:3c:eb:20.
Are you sure you want to continue connecting (yes/no)? yes
nginx | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```
- создал файл кофнигурации [ansible.cfg](), настроил параметр inventory, проверил доступность клиента:
```console

[kita@localhost Otus_Unit_12_Ansible]$ ansible nginx -m ping
nginx | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
[kita@localhost Otus_Unit_12_Ansible]$
```
- 
