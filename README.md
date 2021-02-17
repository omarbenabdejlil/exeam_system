# exeam_system

## partie 1 : 
> les etapes de démarages sont :

| etapes |description |
|--|--|
| 1ère étape | le BIOS. BIOS = Basic Input/Output system : système élémentaire d'entrée/sortie. |
| 2e étape | la MBR. MBR = Master Boot Record : la zone amorce.|
| 3e étape | le GRUB. GRUB = Grand Unified Bootloader : un programme d'amorçage de micro-ordinateur.|
|4e étape | le noyau. |
| 5e étape | init. |
| 6e étape | Runlevel. |
> les niveau de démarages sont :

| runlevel |mode | action |
|--|--|--|
| 0	| Halt |	Shuts down system|
| 1	|Single-User| Mode	Does not configure network interfaces, start daemons, or allow non-root logins|
|2	|Multi-User| Mode	Does not configure network interfaces or start daemons.|
|3	|Multi-User| Mode with Networking	Starts the system normally.|
|4	|Undefined|	Not used/User-definable|
|5 	|X11	|As runlevel 3 + display manager(X)|
|6	|Reboot|	Reboots the system|

