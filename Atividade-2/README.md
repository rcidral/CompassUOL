# Atividade 2

# Instalação da máquina virtual secundária utilizando o VMBox, com um sistema Oracle Linux 8.6.

# Configuração da máquina:
-	RAM: 4096mb
-	DISCO: 40gb
-	Hostname: elklabsec

# Configuração de disco:
-	Swap - 4gb --> swap
-	/boot/efi - 512mb --> EFI system
-	/boot - 1024mb --> xfs
-	/var - 6gb --> xfs
-	/tmp 2gb --> xfs
-	/home - 1.5gb --> xfs
-	/ - 15gb --> xfs

![image](https://user-images.githubusercontent.com/108689845/180467911-89067c7d-69ed-4ca0-886e-8f341941a946.png)

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

# VM2:

-Adicionando o IP da VM1 no arquivo hosts da VM2, para que haja conexão via DNS na questão de relação de confiança e importação de chave: 

![image](https://user-images.githubusercontent.com/108689845/180336469-79c06949-c22f-4be4-825b-7eb55b7ec81d.png)

- importar a chave pública da VM1 para VM2, criando o arquivo authorized_keys para validação da chave com o comando: ssh rcidral@elklabmonitoriacontainer cat /home/rcidral/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys 
- configurar as permissões do arquivo authentication_keys, para que seja gravável apenas pelo usuário rcidral2, porém execultável por todos, com o comando: chmod  755 ~/.shh/authorized_keys

![image](https://user-images.githubusercontent.com/108689845/180337777-616fcca3-816d-48f2-81b7-22f62d332d6d.png)
