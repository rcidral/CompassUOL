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
