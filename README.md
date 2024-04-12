# Вопросы/Ответ
1. Оставил бы Ansible, так как:
   1. Удобно читать YAML-формат;
   2. Push-Метод - Не приходится ждать сработки от IaC Pull, и не требуется вручную вызывать агент на ВМ;
   3. С помощью Terraform. удобно сразу подготовить ВМ с ssh-ключом от сервисной учетной записи Ansible.
2. С помощью готовых ролей из Ansible-Galaxy.

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