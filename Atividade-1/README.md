# Atividade 1

# Instalação da máquina virtual utilizando o VMBox, com um sistema Oracle Linux 8.6.

# Configuração da máquina:
-	RAM: 4096mb
-	DISCO: 40gb
-	Hostname: elklabmonitoriacontainer

# Configuração de disco:
-	Swap - 4gb --> swap
-	/boot/efi - 512mb --> EFI system
-	/boot - 1024mb --> xfs
-	/var - 6gb --> xfs
-	/tmp 2gb --> xfs
-	/home - 1.5gb --> xfs
-	/ - 15gb --> xfs
-	/var/lib/docker - 10gb --> ext4

# Bloquear acesso SSH para root e configurar o SSH:
-	Editar o arquivo sshd_config
-	Descomentar a linha PermitRootLogin e deixa-lo com valor: no
-	Configurando o redirecionamento de portas:

![image](https://user-images.githubusercontent.com/108689845/179813903-be572f3f-b1b6-4644-9db4-ad5a13a744ae.png)

# Ajustar DNS:
-	Editar o arquivo hosts do Windows e do Linux, adicionando a linha: 127.0.0.1 elklabmonitoriacontainer

# Ajustar rede:
-	Modo NAT nas configurações de rede da VM:

![image](https://user-images.githubusercontent.com/108689845/179814040-e833b703-e7dc-4aaa-9a9f-633fb6abf325.png)

- Configurando a rede da maquina virtual para um cidr/24, sob protocolo IPv4 (ignorando o IPv6), utilizando um range classe A e configurando IP fixo:

![image](https://user-images.githubusercontent.com/108689845/179814138-d8f1e1a6-366f-4579-84e5-6712a6bde095.png)

-	Visualizando o arquivo de configuração de rede para a verificação se está tudo correto:

![image](https://user-images.githubusercontent.com/108689845/179814226-4d91e1b3-4826-4b6b-ab31-a03c0142ddfe.png)

# Baixando Docker:
-	sudo dnf update
-	sudo dnf install yum-utils -y
-	sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
-	sudo dnf update
-	sudo dnf install docker-ce docker-ce-cli containerd.io
-	sudo systemctl start docker
-	sudo systemctl enable docker
-	shutdown -r now
-	systemctl status docker

# Adicionando o usuário ao grupo para não precisar usar o Docker como root:
-	sudo groupadd docker
-	sudo usermod -aG docker nome_do_usuário
-	newgrp docke

# Instalar imagem ELK e subi-la para que toda vez que o sistema for iniciado, a imagem inicie junto:
-	docker pull sebp/elk
-	docker images
- Verificar o ID da imagem
-	docker run -d --restart unless-stopped -p 5601:5601 -p 9200:9200 -p 5044:5044 -it id_imagem
-	docker ps
