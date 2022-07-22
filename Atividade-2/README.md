# Atividade 2

# Criação de um clone da máquina virtual original através do VMBox, para ser utilizado como segunda VM:
- Utilizando a opção CLONAR do VMBox, clonando o Estado Atual da máquina.

![image](https://user-images.githubusercontent.com/108689845/180272800-182a3758-4d12-4259-99ee-10ee0ace67e0.png)

# Ajustando máquina virtual principal (VM1) para conexão via SSH e ajustes de rede:

# Ajustar DNS:
-	Editar o arquivo hosts do Linux e do Windows, adicionando a linha: 192.168.0.2 elklabmonitoriacontainer

- Linux ( caminho: /etc/hosts ):

![image](https://user-images.githubusercontent.com/108689845/180335230-af577e3d-b6a5-4003-9d35-a99284e66972.png)

- Windows ( caminho: C:\Windows\System32\drivers\etc ): 

![image](https://user-images.githubusercontent.com/108689845/180335248-b18b591f-a5c9-4cf5-96dd-479b654af721.png)

#Ajustar rede:
- Comando: nmtui

![image](https://user-images.githubusercontent.com/108689845/180335266-da197ff6-6f78-4dfb-8743-243a7cffdccc.png)

- Mudar a rede de modo NAT para BRIDGE no VMBox:

![image](https://user-images.githubusercontent.com/108689845/180335318-8d3997d3-33aa-4106-a2e2-888b36eb9d38.png)
