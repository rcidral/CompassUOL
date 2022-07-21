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
