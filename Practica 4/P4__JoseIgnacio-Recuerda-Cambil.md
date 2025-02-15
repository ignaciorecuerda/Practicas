#PRÁCTICA 4

##Monitorización usando **ab**
### Monitorización en **máquina individual**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 ab -n 100000 -c 100 http://10.211.55.31 

### Monitorización con **ab** en **granja (nginx)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 ab -n 100000 -c 100 http://10.211.55.33 

la carga de cpu del balanceador es 10%
la carga de cpu de uno de los servidores finales es 9.7%

### Monitorización con **ab** en **granja (haproxy)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 ab -n 100000 -c 100 http://10.211.55.33 

#### TIME TAKEN FOR TESTS (seg)
![imagen TIME TAKEN FOR TESTS (seg)](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/ab/imagenes%20graficas/ab-TIME%20TAKEN%20FOR%20TESTS%20(seg).png)

#### TIME PER REQUEST (ms)
![imagen TIME PER REQUEST (ms)](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/ab/imagenes%20graficas/ab-TIME%20PER%20REQUEST%20(ms).png)

#### REQUEST PER SECOND (seg)
![imagen REQUEST PER SECOND (seg)](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/ab/imagenes%20graficas/ab-REQUEST%20PER%20SECOND%20(seg).png)

#### FAILED REQUESTS
![imagen FAILED REQUESTS](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/ab/imagenes%20graficas/ab-FAILED%20REQUESTS.png) 




##Monitorización usando **httperf**
### Monitorización en **máquina individual**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 httperf --server 10.211.55.31 --port 80 --uri /index.html --rate 150 --num-conn 2700 --num-call 1 --timeout 5 

### Monitorización con **ab** en **granja (nginx)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 httperf --server 10.211.55.33 --port 80 --uri /index.html --rate 150 --num-conn 2700 --num-call 1 --timeout 5 

### Monitorización con **ab** en **granja (haproxy)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 httperf --server 10.211.55.33 --port 80 --uri /index.html --rate 150 --num-conn 2700 --num-call 1 --timeout 5 

#### TOTAL CONNECTIONS
![imagen TOTAL CONNECTIONS](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/httperf/imagenes%20graficas/httperf-TOTAL%20CONNECTIONS.png)

#### TOTAL REPLIES
![imagen TOTAL REPLIES](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/httperf/imagenes%20graficas/httperf-TOTAL%20REPLIES.png)

#### REQUEST RATE (seg)
![imagen REQUEST RATE](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/httperf/imagenes%20graficas/httperf-REQUEST%20RATE%20(seg).png)

#### ERRORS TOTAL
![imagen ERRORS TOTAL](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/httperf/imagenes%20graficas/httperf-ERRORS%20TOTAL.png)




##Monitorización usando **Siege**
### Monitorización en **máquina individual**
Las pruebas las hemos hecho ejecutando el siguiente comando:
* siege -c100 -t15S 10.211.55.31 

### Monitorización con **ab** en **granja (nginx)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 siege -c100 -t15S 10.211.55.33 

### Monitorización con **ab** en **granja (haproxy)**
Las pruebas las hemos hecho ejecutando el siguiente comando:
 siege -c100 -t15S 10.211.55.33 

#### ABAILABILITY (%)
![imagen ABAILABILITY](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/siege/imagenes%20graficas/siege-ABAILABILITY%20(%25).png)

#### ELAPSED TIME (seg)
![imagen ELAPSED TIME](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/siege/imagenes%20graficas/siege-ELAPSED%20TIME%20(seg).png)

#### THROUGHPUT (MB/seg)
![imagen THROUGHPUT](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/siege/imagenes%20graficas/siege-THROUGHPUT%20(MB:seg).png)

#### FAILED TRANSACTION
![imagen FAILED TRANSACTION](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/siege/imagenes%20graficas/siege-FAILED%20TRANSACTION.png)


##Cuestión opcional: **JMeter**
En la captura se muestra el gráfico de resultados de las 3 pruebas realizadas con JMeter.
![imagen valorespordefecto](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/jmeter/peticion_http.png)

![imagen graficoderesultados](https://github.com/ignaciorecuerda/Practicas/blob/master/Practica%204/jmeter/graficoderesultados.png)


