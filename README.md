# utn-devops
## Equipo 1 - practica 1

### Proyecto
Automatizar la puesta en marcha de un servicio web, montando una página estatica utilizando Vagrant y apache.  
Se accede a servicio de la máquina guest desde host (localhost:8080) y además, se debe sincronizar la carpeta "/vagrant" de la máquina guest con la carpeta del proyecto en la máquina host

### Integrantes
- Leonardo Maresca
- Juan M. Mateu Arroyo
- Marcelo Acevedo
- Cintia A. Mendiberry Marin
- Leandro Merli
- Diego Plaza
- Rhonal Chirinos

### Requisitos
Probado en un entorno con sistema operativo Windows 10 Pro
1. Vagrant 
2. Oracle Virtual Box 
3. Git

### Como ejecutar el proyecto
1. En SO Windows, desactivar la funcion Hyper-V para operar con maquinas virtuales. En la consola CMD:
> bcdedit /set hypervisorlaunchtype off


2. Clonar este proyecto en un directorio local

> git clone https://github.com/UTN-Devops-Grupo1/utn-devops/tree/unidad-1-vagrant
>
> cd utn-devops
3. Provisionar la máquina virtual con el comando:

> vagrant up --provision

4. Probar conexión ssh y carpeta compartida. Al crear un archivo en /vagrant/ de la máquina guest se verá este mismo archivo en la carpeta del proyecto en la maquina host

> vagrant ssh
>
> touch /vagrant/prueba.txt

5. En el host, acceder con un browser a localhost:8080 y se deberá ver la pagina montada en la maquina guest

### Funcionamiento
- __Vagrantfile__ - Archivo de configuración de Vagrant.    Contiene la configuracion inicial de la máquina virtual que será creada por Vagrant y VBox, incluidos la configuración ssh, sincronización de carpetas, forwardeo de puertos, memoria RAM, copia de archivos y scripts de aprovisionamiento.   
Para informacion detallade acceder a la [documentacion oficial](https://developer.hashicorp.com/vagrant/docs/vagrantfile) de Vagrant

- __Vagrant.bootstrap.sh__ - Script de aprovisionamiento    
Este archivo es invocado por el vagrantfile y cumple la responabilidad de instalar el software necesario para montar el servicio web en la maquina guest.    Actualiza los paquetes e instala git y apache, configura la memoria swap, monta la configuración del servidor web y descarga mediante git la página estática que se monta en este servicio.

- __Configs/devops.site.conf__ - Configuración del servidor web    
Contiene las directivas del servidor web apache. Este archivo es copiado por el vagrant file a /tmp y luego es copiado por el script de aprovisionamiento a la configuracion del servidor web.# utn-devops
