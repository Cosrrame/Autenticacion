# README - Configuración de Servidor Web con Nginx en Vagrant

Este proyecto configura un servidor web con Nginx en una máquina virtual Debian usando Vagrant. Se utiliza un repositorio GitHub para alojar un sitio estático.


## Pasos para Ejecutar



### Iniciar la máquina virtual

   
   vagrant up
   

### Acceder a la máquina virtual

   vagrant ssh


### Acceder al sitio web

   Cambiamos el archivo hosts a:
		192.168.57.10 		mrm  www.mrm www.mrm.com mrm.com
		192.168.57.10 		perfectLearn  www.perfectLearn www.perfectLearn.com perfectLearn.com

   Abre tu navegador y accede a `http://mrm`, y te saldrá un 403 Forbidden
   
   Abre tu navegador y accede a `http://perfectLearn`, y te saldrá la página de Perfect Learn

   


## Capturas

### Capturas del log
![alt text](images/logs.png)
### Capturas de la autorización en contact

la página carga correctamente, pero cuando hacemos clic en contact...

![alt text](images/form1.png)

Una vez autoizados...

![alt text](images/form2.png)