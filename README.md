# Протестированно на Rocky Linux 9

# prepare before start playbook
- type a variable value to:
```
./roles/postgresql/dafaults/main.yml
```
- make file and type telegram a "token" and "chat_id":
```
touch ./roles/sendTgMessage/dafaults/main.yml

cat <<EOF >> ./ansbile.cfg 
token: " "
chat_id: " "
EOF
```
- make file and set group "web_servers":
```
touch ./inventories/production/inventory.ini

cat <<EOF >> ./ansbile.cfg 
[web_servers]
8.8.8.8
EOF
```
- set inventory path and remote_user to ./ansible.cfg:
```
touch ./ansible.cfg

cat <<EOF >> ./ansbile.cfg 
[defaults]
inventory = ./inventories/production/inventory.ini
remote_user = user
EOF
```

# how to run:
```
ansible-playbook playbook.yml
```
