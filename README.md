# exeam_system

## Partie 1 : 
### Q1/ les etapes de démarages sont :

| etapes |description |
|--|--|
| 1ère étape | le BIOS. BIOS = Basic Input/Output system : système élémentaire d'entrée/sortie. |
| 2e étape | la MBR. MBR = Master Boot Record : la zone amorce.|
| 3e étape | le GRUB. GRUB = Grand Unified Bootloader : un programme d'amorçage de micro-ordinateur.|
|4e étape | le noyau. |
| 5e étape | init. |
| 6e étape | Runlevel. |
### Q2/ les niveau de démarages sont :

| runlevel |mode | action |
|--|--|--|
| 0	| Halt |	Shuts down system|
| 1	|Single-User| Mode	Does not configure network interfaces, start daemons, or allow non-root logins|
|2	|Multi-User| Mode	Does not configure network interfaces or start daemons.|
|3	|Multi-User| Mode with Networking	Starts the system normally.|
|4	|Undefined|	Not used/User-definable|
|5 	|X11	|As runlevel 3 + display manager(X)|
|6	|Reboot|	Reboots the system|

### Q3/ la structure de disque est la suivante : 

|partion | point de montage | type de systeme de ficher | description |
|--|--|--|--|
| /dev/sda1 | /mnt/win_c | ntfs | partiotion __primaire__ rendre a windows "partiotion "C" |
| /dev/sda5 | /mnt/win_d | ntfs | partiotion __logique__ rendre a windows "partiotion "D" |
| /dev/sda6 | / | ext3 | partiotion __primaire__ rendre a Linux |
| /dev/sda7 | --- | swap | partiotion logique rendre de type _SWAP_ |

### Q4/ cette ligne signifie que :
`30  12  1-7  *  7  archiver.sh` 
> cette ligne siqgnifie que le scripte `archiver.sh` doit etre exécuter `chaque dimanche` de `n'importe qu'elle Mois` à partir du `jour 1` jusqu'a le `jour 7` et à l'heure `12:30`

<hr>

## Partie 2 : réseau : 
### Q1/ :
> l'adresse réseau de l'hote 172.20.2.104/27 est `172.20.2.96` et l'adress de diffusion est `172.20.2.127` 
### Q2/ :
> le nom du fichier de config est `/etc/network/interfaces` ou bien `/etc/netplan/50-cloud-init.yaml` dans Ubuntu 18-20 .
### Q3/ Configuration de l'interfaces de __serveur 1__ :
```bash
# The loopback network interface
auto lo
iface lo inet loopback

# la premier interface
iface eth0 inet static
      address 192.168.1.3
      netmask 255.255.255.0
      gateway 192.168.1.1
      
# la deuxieme interface     
      iface eth1 inet static
      address 192.168.2.3
      netmask 255.255.255.0
      gateway 192.168.2.1
      
# la troisieme interface     
      iface eth2 inet static
      address 192.168.3.3
      netmask 255.255.255.0
      gateway 192.168.3.1
```
### Q4/ : 
> Pour consideré la configuration il faut redemarrer le service `networking` :
```bash
service networking restart 
```
### Q5/ : 
> il faut attribuer le `net.ipv4.ip_forward = 1` pour suivre les paquets comme un routeur a travers le réseau 

### Q6/ : c'est La commande `sudo route` 
> le routage se fait a travers le serveur 1 , puiqu'il est le `relais` , voila la config sur D1:
`route add -net 192.168.1.0/24 gw 192.168.2.3 dev enp0s3`
`route add -net 192.168.3.0/24 gw 192.168.2.3 dev enp0s3`


> la config sur P1 comme exemple de pool P1-Px : 
`route add -net 192.168.2.0/24 gw 192.168.1.3 dev enp0s3`
`route add -net 192.168.3.0/24 gw 192.168.1.3 dev enp0s3`


### Q7/ : 
il faut rendre le serveur dans la liste `/etc/resolve.conf` pour le consulter automatiquement ! , voila la ligne qu'il faudra ajouter : 
```bash
nameserver 172.40.3.2
```
