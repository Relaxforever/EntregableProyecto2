# info de la materia: ST0263 Topicos Especiales en Telematica

# Estudiante(s): nombre, email-eafit

Juan Andres Henao jahenaod@eafit.edu.co

Fidel Fernando Caicedo Castaño ffcaicedoc@eafit.edu.co

Sebastian Velez Galeano svelezg4@eafit.edu.co

# Profesor: nombre, email-eafit

ALVARO ENRIQUE OSPINA SANJUAN aeospinas@eafit.edu.co

#

# nombre del proyecto, lab o actividad

#### Cluster Kubernetes de Alta Disponibilidad para WordPress

#

# 1. breve descripción de la actividad

Desplegar la misma aplicación del Reto 4 en un cluster de alta disponibilidad en

Kubernetes desplegado como IaaS con la distribución microk8s configurando tu propio

clúster de kubernetes.

Se implementó un sistema de gestión de contenidos WordPress en un entorno de alta disponibilidad utilizando Kubernetes como infraestructura como servicio (IaaS). El clúster Kubernetes se distribuyó en múltiples máquinas virtuales y se construyó con la distribución microk8s. Se tuvieron en cuenta aspectos clave como los volúmenes compartidos y la gestión del acceso externo mediante Ingress.

Nginx se utilizó como balanceador de carga y se configuró con un objeto Ingress para dirigir el tráfico HTTP/S a los servicios internos del clúster. La arquitectura incluyó dos instancias de WordPress, una instancia de base de datos MySQL y un sistema de archivos distribuido NFS para el almacenamiento.

Este proyecto se basó en tecnologías como Kubernetes, proveedores de dominio como **Ionos** y servicios de GCP, con instancias.

![enter image description here](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQIXZI_O9JOIOKXN3vVRfvYq880v4a0CVmXb4mZA8mF&s)

#

## 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

- **Despliegue exitoso en clúster Kubernetes:** La aplicación WordPress se ha implementado con éxito en un clúster Kubernetes de alta disponibilidad, utilizando microk8s como distribución.
- **Balanceo de carga con Nginx:** Se ha configurado Nginx como balanceador de carga para distribuir el tráfico HTTP/S entre las instancias de WordPress, mejorando el rendimiento y la tolerancia a fallos.
- **Almacenamiento persistente con NFS:** Se ha implementado un sistema de archivos distribuido NFS para garantizar la persistencia de los datos de WordPress y MySQL, incluso en caso de reinicio o fallo de los pods.
- **Gestión de acceso externo con Ingress:** Se ha configurado un objeto Ingress para controlar el acceso externo al clúster, permitiendo el enrutamiento del tráfico a los servicios internos de manera segura y eficiente.
- **Certificados SSL:** Se han obtenido e implementado certificados SSL de Let's Encrypt para asegurar la comunicación entre el cliente y el servidor, protegiendo la información sensible.

#

## 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

Se cumplio todo.

## 2. información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.

La arquitectura del sistema se basa en los siguientes componentes:

- **Nodos Kubernetes:**
  - 1 Nodo Master: Responsable de la gestión y coordinación del clúster.
  - 2 Nodos Workers: Ejecutan las cargas de trabajo (pods) de WordPress y MySQL.
- **Servicios:**
  - WordPress: Dos instancias replicadas para alta disponibilidad.
  - MySQL: Una instancia replicada para alta disponibilidad.
  - Nginx: Balanceador de carga y controlador de Ingress.
- **Almacenamiento:**
  - NFS: Sistema de archivos distribuido para almacenar los datos de WordPress y MySQL.
- **Red:**
  - Ingress: Controla el acceso externo al clúster y dirige el tráfico a los servicios internos.

![enter image descripddaadtion here](https://i.ibb.co/v3S5bKd/microk8s-arc-3.jpg)

A partir de la internet en nuestra dirección https://proyecto2.reto3jahenaod.com/ con el certificado SSL anteriormente explicado Ingresamos a un cluster creado microk8s que cuenta con 4 instancias, tres nodos un master y 2 workers e ingresamos a traves de ingress y entramos al balanceador de carga el cual nos reparte los 2 pods de workpress y cada uno tiene su claim del persistent volume y estas apuntan a un persistent volume que nos lleva al nfs y también estas le pegan a un pod corriendo nuestro MySQL ccon su persistent volume para el nfs tambien

## 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

Se utilizo Micro k8 para el desarrollo

- Se utilizo Nginx

- Se utilizo el Lenguaje de scripts Yaml

- Se utilizo NFS Kernel server

- Para la certificación utilizamos **lets-encrypt**

#

- **Distribución Kubernetes:** microk8s
- **Orquestador de Contenedores:** Kubernetes
- **Lenguaje de Configuración:** YAML
- **Balanceador de Carga:** Nginx
- **Servidor NFS:** NFS Kernel Server
- **Base de Datos:** MySQL
- **Certificados SSL:** Let's Encrypt

![enter image description here](https://media.discordapp.net/attachments/1011350535531667477/1241792381016346634/image.png?ex=664b7cc7&is=664a2b47&hm=17a550be1ec760ecd69198afc2fe5f37bbe565fb4afa88c660beb703e9c146da&=&format=webp&quality=lossless&width=720&height=582)

## como se compila y ejecuta.

### Se aplican cada uno de los manifestos YAML en este siguiente orden:

![enter image description here](https://media.discordapp.net/attachments/1011350535531667477/1241781669782880416/image.png?ex=664b72cd&is=664a214d&hm=1a2fb2cd6faf53855b7aa2e03ac1a3e4532b609b23d6d3ef003d9b6263ac43c0&=&format=webp&quality=lossless)

- Servidor NFS

- Base de datos SQL

- Wordpress

- Nginx para resolución de DNS

_Nota: Cada uno de estos tiene posee su respectiva sección para gestionar services, pvc y deployment_

# referencias:

[Kubernetes the Easy way](https://www.securityandit.com/network/kubernetes-the-easy-way-part-01/)

[https://microk8s.io/](https://microk8s.io/ "https://microk8s.io/")

[https://medium.com/@somashekarvedadevops/wordpress-deployment-using-microk8s-7218e2801899](https://medium.com/@somashekarvedadevops/wordpress-deployment-using-microk8s-7218e2801899 "https://medium.com/@somashekarvedadevops/wordpress-deployment-using-microk8s-7218e2801899")
https://microk8s.io/docs/clustering
https://microk8s.io/docs/how-to-nfs
https://www.youtube.com/watch?v=TlHvYWVUZyc
https://www.youtube.com/watch?v=GPVH9fHW0Dk
https://microk8s.io/
https://zhuzean.medium.com/microk8s-on-gcp-vm-730aa49d277f

## sitio1-url

[https://www.reto3jahenaod.com/](https://www.reto3jahenaod.com/ "https://www.reto3jahenaod.com/")

## sitio2-url

[https://proyecto2.reto3jahenaod.com/](https://proyecto2.reto3jahenaod.com/ "https://proyecto2.reto3jahenaod.com/")

## url de donde tomo info para desarrollar este proyecto

https://github.com/st0263eafit/st0263-241
