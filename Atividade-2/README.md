# Atividade 2

# Criação de um clone da máquina virtual original através do VMBox, para ser utilizado como segunda VM:
- Utilizando a opção CLONAR do VMBox, clonando o Estado Atual da máquina.

![image](https://user-images.githubusercontent.com/108689845/180272800-182a3758-4d12-4259-99ee-10ee0ace67e0.png)

# Ajustando máquina virtual principal (VM1) para conexão via SSH e ajustes de rede:

# Ajustar DNS:
-	Editar o arquivo hosts do Linux e do Windows, adicionando a linha: 192.168.0.8 elklabmonitoriacontainer

- Linux ( caminho: /etc/hosts ):

![image](https://user-images.githubusercontent.com/108689845/180335230-af577e3d-b6a5-4003-9d35-a99284e66972.png)

- Windows ( caminho: C:\Windows\System32\drivers\etc ): 

![image](https://user-images.githubusercontent.com/108689845/180335248-b18b591f-a5c9-4cf5-96dd-479b654af721.png)

#Ajustar rede:
- Comando: nmtui

![image](https://user-images.githubusercontent.com/108689845/180335266-da197ff6-6f78-4dfb-8743-243a7cffdccc.png)

- Mudar a rede de modo NAT para BRIDGE no VMBox:

![image](https://user-images.githubusercontent.com/108689845/180335318-8d3997d3-33aa-4106-a2e2-888b36eb9d38.png)

# Ajustando máquina virtual secundária (VM2) para conexão via SSH e ajustes de rede:

# Ajustar DNS:
-	Editar o arquivo hosts do Linux e do Windows, adicionando a linha: 192.168.0.9 elklabsec

- Linux ( caminho: /etc/hosts ):

![image](https://user-images.githubusercontent.com/108689845/180335481-37583712-d0e9-4807-8c23-d2cedde44269.png)

- Windows ( caminho: C:\Windows\System32\drivers\etc ): 

![image](https://user-images.githubusercontent.com/108689845/180335520-2adffe88-961d-4f41-b6fe-0f93876f5d3d.png)

#Ajustar rede:
- Comando: nmtui

![image](https://user-images.githubusercontent.com/108689845/180335552-aa68f40e-ae85-464f-afa8-2fd59738d7b1.png)

- Mudar a rede de modo NAT para BRIDGE no VMBox:

![image](https://user-images.githubusercontent.com/108689845/180335607-71f7ee95-1e1a-432c-804d-da4a287e92d3.png)

# Criar relação de confiança entre as duas VMs:

# VM1: 

Criação das chaves:
- ssh-keygen 
- chaves armazenadas em /home/rcidral/.ssh/

![image](https://user-images.githubusercontent.com/108689845/180104196-e4391865-15a5-4ff8-9cce-239d2a42d1e4.png)

- adicionar o IP da VM2 no arquivo hosts da VM1, para que haja conexão ssh via DNS na questão de relaçao de confiança:

![image](https://user-images.githubusercontent.com/108689845/180336198-0a3a8597-34bd-4be6-9860-945dfe49adff.png)
