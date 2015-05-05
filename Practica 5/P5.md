#PRÁCTICA 5

##Creación de la base de datos
Para ello hemos seguido tal cual los comandos que se indican en el guión de prácticas.

##Replica de una Base de Datos con MySQL con mysqldump
Para hacer la replica de la BD hemos usado los siguientes comandos:
1.- mysql -u root –p (entramos en mysql)
2.- FLUSH TABLES WITH READ LOCK; (para que nadie pueda modificar la BD)
3.- exit (salimos de mysql)
4.- mysqldump contactos -u root -p > /home/apozo/contactos.sql (para realizar la copia)
5.- mysql -u root –p (entramos nuevamente en mysql)
6.- UNLOCK TABLES;
7.- exit (salimos de mysql)


Seguidamente, desde la máquina 2, introducimos la orden para copiar la base de datos a esta máquina:
sudo scp apozo@10.211.55.31:/home/apozo/contactos.sql /root/

A continuación, en la máquina 2, antes de restaurar la base de datos tenemos que crearla (porque mysqldump no mete las ordenes de crear la base de datos).
Hemos introducido estas ordenes:
1.- mysql -u root -p
2.- create database contactos;
3.- mysql -u root -p contactos < /root/contactos.sql

Seguidamente configuramos el archivo my.cnf tanto del maestro como del esclavo con la configuración indicada para versión 5.5 o superiores.

Ahora tenemos que crear un usuario en la máquina del maestro y darle permisos, para ellos ejecutamos:
1.- CREATE USER esclavo IDENTIFIED BY 'esclavo';
2.- GRANT REPLICATION SLAVE ON *.* TO 'esclavo'@'%' IDENTIFIED BY 'esclavo';
3.- FLUSH PRIVILEGES;
4.- FLUSH TABLES;
5.- FLUSH TABLES WITH READ LOCK;

en la maquina del cliente hacemos:
1.- entramos en mysql
2.- CHANGE MASTER TO MASTER_HOST='10.211.55.31', MASTER_USER='esclavo', MASTER_PASSWORD='esclavo', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=501, MASTER_PORT=3306;
3.- arrancamos el esclavo.
4.- UNLOCK TABLES;(en la maquina maestro)
5.- start slave (en el esclavo)


Tuvimos el problema número 1236 porque hicimos inserciones antes de cambiar el master con el comando CHANGE MASTER. Después de modificar el master_log_file y el master_log_pos a las posiciones actualizadas después de la inserción el esclavo, ha funcionado sin problemas. Notamos la diferencia que no se ha transferido la tupla que insertamos antes de configurar bien el esclavo.


