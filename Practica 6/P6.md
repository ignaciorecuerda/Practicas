#PRÁCTICA 6

##Configuración del RAID por software
Primero hemos añadido dos discos a la máquina virtual mediante a interfaz de Parallels.
Instalamos mdadm con el comando:
sudo apt-get install mdadm
Y seguidamente tecleamos el siguiente comando para crear el RAID 1:
sudo mdadm -C /dev/md0  --level=raid1 --raid-devices=2 /dev/sdb /dev/sdc

![imagen crear md0 (crear_raid1.png)](direccion github)

y vemos los detalles:
![imagen detalles md0 (raid_state.png)](direccion github)

Una vez creado nuestro RAID le damos formato con el comando:
sudo mkfs /dev/md0

y después creamos el directorio que vamos a montar para el RAID al que le hemos dado el nombre "datos". Lo montamos con el comando:
sudo mount /dev/md0 /datos

Por último modificamos el archivo /etc/fstab para montar el RAID automáticamente cada vez que iniciemos el sistema. Para ello añadimos en la última línea del fichero mencionado lo siguiente:
UUID=6291710f-e655-4275-b1af-b9bbd441448f /datos ext2

A continuación explicamos con imágenes el proceso que se ha seguido para comprobar que el RAID funciona correctamente:

#### Desactivar y eliminar uno de los discos
![imagen raid_test1.png](direccion github)

#### Añadimos el disco despues de haber modificado el directorio datos
![imagen raid_test2.png](direccion github)

#### Comprobamos que se han sincronizado
![imagen raid_test3.png](direccion github)

