# CRUT


## Descripción del problema
En el ámbito de la industria 4.0 son muchos los sistemas que continúan anclados a un entorno de ejecución que les impiden escalar y mejorar su propio rendimiento.

Son muchos los dispositivos, tecnologías, protocolos y software empleados en el desarrollo de un sistema de control industrial. Una de las principales funciones que se desarrollan en este ámbito esta orientada a la configuración de los dispositivos de control, los cuales necesitan de unos parámetros e información necesaria para poder realizar su cometido.


## Solución propuesta
CRUT (Cloud RTU Universal Tool) nace de la necesidad que hasta el momento el mundo de la industria ha vivido en el marco de la configuración sobre dispositivos de carácter programables como PLCs, RTUs, etc, encargados de controlar el correcto comportamiento de procesos industriales.

Hasta el momento, la parametrización de un dispositivo programable; en este caso particular una RTU, se realiza a través de un software de escritorio el cual debe estar físicamente conectado al dispositivo para poder enviarle los datos de configuración. Este trabajo resulta tedioso ya que la persona responsable de dicha tarea tiene que desplazarse personalmente a la localización donde se encuentren los dispositivos para poder configurarlos.

La herramienta CRUT agiliza todo ese proceso, ya que de este modo no es necesario conectarse físicamente al dispositivo para parametrizarlo. CRUT ofrece una plataforma de configuración remota desde la que es posible realizar dicha tarea en cualquier dispositivo desde cualquier situación con conexión a internet.

CRUT elimina las barreras existentes hasta ahora y agiliza las operaciones de configuración, haciendolas mas ligeras y expandibles.


## Arquitecura software
Se han estudiado los diferentes tipos de [arquitecturas software] (http://jj.github.io/CC/documentos/temas/Arquitecturas_para_la_nube) para evaluar a cual de ellas mejor se adapta la aplicación. Tras un análisis y evaluación de lo que cada una ofrece y teniendo claro lo que el proyecto necesita y cual es su comportamiento, he decidido que la arquitectura de microservicios es la que mas se adapta a las necesidades de mi producto.

Es por esto por lo que se va a utilizar una arquitectura de microservicios basada en una API REST para el desarollo de la plataforma CRUT, empleando para ello el conjunto de tecnologías que la plataforma MEAN ofrece como se muestra en el siguiente imagen:

![alt text](https://raw.githubusercontent.com/jmanday/CRUT/gh-pages/images/arquitectura.png "Arquitectura proyecto")


## Servicios, microservicios y tecnologías
Como se puede apreciar en la imagen, el servidor de este tipo de arquitecturas se componen de dos partes:

- La parte del **backend** donde desarrolla el API REST basado en [Nodejs](https://nodejs.org/es/) y [Express](http://expressjs.com/es/).

- La parte del **frontend** donde se implementa la vista del cliente mediante [Angularjs](https://angularjs.org/).


Para implementar este tipo de arquitectura se va a utilizar la plataforma de servicios [AWS](https://aws.amazon.com/es/). De este modo se tendrá separada la parte del servidor de los microservicios.

El servidor será desplegado en el servicio [Amazon Elastic Beanstalk](https://aws.amazon.com/es/elasticbeanstalk/), en el cual se integran todas las tecnologías necesarias para su desarrollo y funcionamiento.

Por ahora se va a utilizar un sólo microservicio basado en [MongoDB](https://www.mongodb.com/es) donde se van a alojar los datos de las diferentes configuraciones de los dispotivos, y el cual correrá bajo el servicio [Amazon EC2](https://aws.amazon.com/es/ec2/) como una máquina totalmente remota y separada del servidor.



