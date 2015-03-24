#PRÁCTICA 3

##3.1 Instalar nginx en Ubuntu Server 12.04
Hemos seguido lo pasos indicados en el guión de prácticas

##3.2 Balanceo de carga usando nginx
Hemos modificado el archivo de configuración de nginx, indicándole los dos servidores apache, definiendo un nombre para este grupo (dos servidores apache y el balanceador), hemos configurado ip_hash para que peticiones de la misma ip sean atendida siempre por el mismo servidor, no le hemos indicado la carga de trabajo que tiene cada servidor, es decir, ambas van a tener la misma carga de trabajo (weight=1).

Nota:la opción ip_hash se ha descartado, ya que para hacer pruebas las peticiones siempre las vamos a hacer desde la misma máquina y siempre irían a la misma máquina final, no pudiendo comprobar el balanceo.

Como no vamos a tener sesiones de usuario (por ahora) hemos puesto la opción keepalive la cual recibe un tiempo de 10 segundos.


##3.3 Opciones de configuración del nginx para establecer cómo le pasará trabajo a las máquinas servidoras finales
Tras poner la configuración escogida por nosotros, esta ha quedado de la siguiente forma:
![imagen](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%203/balanceador_nginx.png)

Sabemos que al no ser un problema real con aplicaciones y demas únicamente se apreciarían los weight, que en nuestro caso están por defecto (weight=1)

Adjuntamos una captura del balanceo de carga
![imagen muestra balanceo](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%203/balanceador_funcionando.png)

##3.4 Balanceo de carga con haproxy
Instalamos haproxy y lo configuramos tal y como se indica en el guión de prácticas.
Nuestra configuración queda así:
![imagen haproxy](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%203/balanceador_haproxy.png)


