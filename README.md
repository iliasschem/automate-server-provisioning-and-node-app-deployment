# Automate-server-provisioning-and-node-app-deployment

This repos aims to give a simple example of how to automate a server provisioning and node app deployment using Ansible

## Dependencies

- [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) 
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)


## Steps to start the project

- Build you server, run:
```bash
docker-compose up -d
``` 

- Try to connect to the server with ssh:
```bash
ssh root@localhost
```
root password: root

- In 'DevOps/devops/create-user/public-keys' create a new file 'firstName.lastName.pub'

- Add your public key:
```bash
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub
```
copy and past the result to your file 'firstName.lastName.pub'.

- To create the user 'superUser', run command:
```bash
yarn create:user
```
Vault password 'hello'

- Start provisioning your server:
```bash
yarn provision
```

- To deploy your application:
```bash
yarn deploy
```

- To connect to your server:
```bash
ssh superUser@localhost
```
Now you are connected to the server. You can check if you application is deployed.

## More info

- To encrypt you password using Ansible vault, run:
```bash
 ansible-vault encrypt_string '***Password***'
```
in our case we encrypt the superUser password, you can find the result in 'DevOps/devops/create-user/vars/main.yml'
the vault password used is 'hello'
