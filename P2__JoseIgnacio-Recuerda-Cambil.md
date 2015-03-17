#PRACTICA 2
##Para realizar el punto 2 de la práctica (Crear un tar con ficheros locales en un equipo remoto) hemos puesto el siguiente comando:
tar czf - /home/apozo/Desktop/hola.html | ssh apozo@10.211.55.32  'cat > ~/tar.tgz' 

##Para realizar el punto 3 de la práctica (Instalar la herramienta rsync) hemos seguido los siguientes pasos:
1º hemos comprobado que teníamos instalado esa herramienta
2º hemos actualizado, con sudo apt-get update, para asegurarnos de tener la última versión de ese y de todos nuestras aplicaciones.
3º hemos ejecutado en ambas máquinas(“backup” y “principal”) el comando: sudo passwd root 
4º en la máquina “backup” ejecutamos el siguiente comando: rsync -avz -e ssh apozo@10.211.55.31:/var/www /var/www 
y con esto conseguimos clonar el directorio de la máquina “principal” a la máquina “backup”.
5º hacer un crontab para que se ejecute la acción del paso 4 cada cierto tiempo indicado por nosotros.

##Para realizar el punto 4 de la práctica 
1º ssh-keygen -t dsa (“backup”)
2º chmod 600 ~/.ssh/authorized_keys
3ºssh-copy-id -i .ssh/id_dsa.pub apozo@10.211.55.31
nos dice que se ha instalado y nos pide la contraseña que pusimos en el “sudo passwd root”
3ºrsync -avz -e ssh root@10.211.55.31:/var/www/ /var/www/

Ponemos captura de pantalla de los comandos ejecutados
[/sshsinpass.png]

Problema solucionado: no nos dejaba hacer el rsync como root y hemos tenido que hacerlo con nuestro usuario (apozo). Y después de hacer “ssh-copy-id -i .ssh/id_dsa.pub apozo@10.211.55.31” hemos tenido que conectarnos a la máquina con “ssh apozo@10.211.55.31” nos pide la contraseña, la introducimos, nos salimos con “exit” y justo después ejecutamos el comando “ssh add”. gracias a esto conseguimos poder conectarnos a la máquina “principal” sin tener que introducir la contraseña. 

##Para realizar el punto 5 de la práctica (Programas tareas con crontab)
1º Nos hemos identificado como root “sudo su”
2º hemos editado el archivo /etc/crontab y hemos añadido  la última linea de la siguiente imagen (indica que se ejecutara cada minuto).
[/crontab.png]
