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
