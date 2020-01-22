# Ansible

Para executar o arquivo é preciso ter alguns programas instalados.

Abra o terminal e instale os seguintes:
```
sudo apt install python
sudo apt install python-pip
pip install boto boto3 ansible
```

Crie uma ssh para conectar na AWS.
´´´
ssh-keygen -t rsa -b 4096 -f ~/.ssh/my_aws
´´´

Crie a pasta para armazenar o seu projeto.
´´´
mkdir -p AWS_Ansible/group_vars/all/
cd AWS_Ansible
touch playbook.yml
´´´
Crie o seu Ansible Vault 
```
ansible-vault create group_vars/all/pass.yml
```
Verifique se está tudo indo bem.
```
ansible-playbook playbook.yml --vault-password-file vault.pass
```

Edite o pass.yml para adicionar as chaves de acesso, access_key e secret_key.
```
ansible-vault edit group_vars/all/pass.yml
```
Agora é só rodar.
```
ansible-playbook playbook.yml --ask-vault-pass --tags create_ec2
```