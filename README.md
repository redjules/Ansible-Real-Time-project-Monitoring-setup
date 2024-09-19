# Ansible-Real-Time-project-Monitoring-setup


![Screenshot 2024-09-19 at 23 30 18](https://github.com/user-attachments/assets/5fcbe0d0-79cd-4659-a8ce-c62b5e4a76ed)


We will be creating 2 systems, one will be our Ansible controller machine and the other will be acting as a Target system in our organization.

From our ansible controller will trigger our ansible  playboook which will do all the monitoring setup in the target system and then we can visualize all the tools installed in the target system is working as expected or not.

we create an AWS EC2 machine with 2 instances and Amazon image

![Screenshot 2024-09-20 at 00 13 54](https://github.com/user-attachments/assets/9da0609f-22dc-42e2-b34f-930d7ff4c30c)

we create a new key pair:

![Screenshot 2024-09-20 at 00 15 09](https://github.com/user-attachments/assets/cd28658b-0b54-4697-8096-c59ccb9c3211)


![Screenshot 2024-09-20 at 01 09 56](https://github.com/user-attachments/assets/d5287b96-9174-4cb3-9150-793bdc44bc41)

and launch instances

We edit inbound rules:

![Screenshot 2024-09-20 at 01 11 25](https://github.com/user-attachments/assets/aecd6c45-1346-4a8c-b1d4-d511735665b8)

we have 2 machines, the asnible controller and a node:

![Screenshot 2024-09-20 at 01 12 24](https://github.com/user-attachments/assets/4aff905f-f51b-45d7-9ee3-8981f2192a2a)

we follow the ssh steps to be connected to the EC2 machine:

![Screenshot 2024-09-20 at 01 13 04](https://github.com/user-attachments/assets/60c94f1c-7e98-48e3-910c-cc39e478ceec)

![Screenshot 2024-09-20 at 01 14 20](https://github.com/user-attachments/assets/c4948db2-525d-4966-99a0-913b697797e0)

we install ansible with yum:

![Screenshot 2024-09-20 at 01 15 16](https://github.com/user-attachments/assets/3c478a10-1fed-4ffe-9c3e-43e68bfaed2e)


![Screenshot 2024-09-20 at 01 15 45](https://github.com/user-attachments/assets/7744458e-bf4e-4dbc-95fd-3d47b7bce8f8)


we connect to the node machine with ith ip:


![Screenshot 2024-09-20 at 01 17 21](https://github.com/user-attachments/assets/21da9c80-d3c9-416f-875b-b79d6ef91d73)

![Screenshot 2024-09-20 at 01 17 41](https://github.com/user-attachments/assets/5b47f764-a2fe-4d2a-b7b1-31703601b76d)

![Screenshot 2024-09-20 at 01 19 19](https://github.com/user-attachments/assets/cfc323ef-d096-4c61-8471-3933d57ed233)

![Screenshot 2024-09-20 at 01 18 46](https://github.com/user-attachments/assets/219836b8-e3a2-4d40-912e-8217c156c183)


we want to make the passwordless connectivity between root user 

![Screenshot 2024-09-20 at 01 21 05](https://github.com/user-attachments/assets/06061088-753a-4941-9a65-cc1b6e4879a3)

you copy the content of the public key:

![Screenshot 2024-09-20 at 01 22 10](https://github.com/user-attachments/assets/2b28bc96-3e5a-47bf-bc3d-464534c882a3)


we copy the public key from the controller here and give read and write permission:

![Screenshot 2024-09-20 at 01 24 50](https://github.com/user-attachments/assets/1e8345b1-3021-44d9-a15c-e25992cd257a)

this is the playbook.yml that has 4 roles:

![Screenshot 2024-09-20 at 01 29 14](https://github.com/user-attachments/assets/235b370e-3fc1-4871-9ee1-b0555ff2aba7)

we run our playbook:

![Screenshot 2024-09-20 at 01 37 57](https://github.com/user-attachments/assets/4e862761-9a0c-4a8c-99fa-0b240821f04c)

![Screenshot 2024-09-20 at 01 38 19](https://github.com/user-attachments/assets/168f4a0b-4ede-406f-ab37-137f685ca7b3)

![Screenshot 2024-09-20 at 01 39 01](https://github.com/user-attachments/assets/ea34c144-fcb7-4b9c-a0ed-e069d578ef2e)


![Screenshot 2024-09-20 at 01 39 34](https://github.com/user-attachments/assets/29f5ee70-0daa-46d4-afef-036f1203b345)

we check status of grafana server, prometheus, alertmanager, node_exporter.service:

![Screenshot 2024-09-20 at 01 39 45](https://github.com/user-attachments/assets/a73db9ec-e1de-4a67-b4e4-5058725a4dad)


we get into grafana:

![Screenshot 2024-09-20 at 01 41 25](https://github.com/user-attachments/assets/7c198ac8-9021-4eca-8bb3-17726e55e696)

we check Prometheus:


![Screenshot 2024-09-20 at 01 42 41](https://github.com/user-attachments/assets/0563c9a8-ef1e-446f-a173-ef9926506800)

and node Exporter:

![Screenshot 2024-09-20 at 01 43 06](https://github.com/user-attachments/assets/ba519738-4b27-4165-b2b2-251f4dcc228d)

and alertmanager:

![Screenshot 2024-09-20 at 01 43 37](https://github.com/user-attachments/assets/bb157613-07c4-4cb7-84d1-8fda7d522b9e)

