# Atividade 2

# Criação de um clone da máquina virtual original através do VMBox, para ser utilizado como segunda VM:
- Utilizando a opção CLONAR do VMBox, clonando o Estado Atual da máquina.

![image](https://user-images.githubusercontent.com/108689845/180272800-182a3758-4d12-4259-99ee-10ee0ace67e0.png)

# Ajustando máquina virtual principal (VM1) para conexão via SSH e ajustes de rede:

# Ajustar DNS:
-	Editar o arquivo hosts do Linux e do Windows, adicionando a linha: 192.168.0.2 elklabmonitoriacontainer

- Linux ( caminho: /etc/hosts ):

![image](https://user-images.githubusercontent.com/108689845/180109544-7ed8cc0e-c3fe-445c-b783-b7958be18114.png)

- Windows ( caminho: C:\Windows\System32\drivers\etc ): 

![image](https://user-images.githubusercontent.com/108689845/180274531-17147517-f9b8-45d1-b7b9-a60a99e45204.png)

#Ajustar rede:
- Comando: nmtui

![image](https://user-images.githubusercontent.com/108689845/179824759-bddf00cd-9c4b-48a7-b9ca-81c462f6f0ca.png)

- Mudar a rede de modo NAT para BRIDGE no VMBox:

![image](https://user-images.githubusercontent.com/108689845/180000178-457ad7bd-df74-424d-ab98-f1563503f5e3.png)
