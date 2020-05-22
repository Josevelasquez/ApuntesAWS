# AWS Compute services

Representado atravez de los siguientes servicios:

![Compute Services](./assets/ComputeService.PNG)


## 1. Amazon EC2

Es el recurso primario de computo, este provee servicios remotos de computo, con el completo control sobre el redimensionamiento de la capacidad según la necesidad.

Podemos clasificar las instancias de EC2 de la siguiente manera:

![Tipos de instancias EC2](./assets/EC2Types.png)

Donde debemos tener en cuenta lo anterior para determinar qué tipo de instancias son las ideales para nuestro proyecto, las instancias de propósito general están orientadas a trabajar aplicaciones con alto tráfico utilizando recursos de cpu y memoria balanceadamente según las necesidades del usuario.

Las instancias de computación optimizada nos ayudan para trabajos computacionales altamente demandados y que requieren de muchos recursos. Las instancias que están orientadas a optimizar el almacenamiento  proveen estas condiciones óptimas para aplicaciones que exigen recursos en altas cantidades ideales para trabajar con dataset.

Gpu optimizado  proveen las condiciones para procesos paralelos que necesiten recursos de gpu como trabajos 3D, Renderizado y procesos multimedia. Las instancias de memoria optimizada son ideales para procesos de analítica y bases de datos  con alta demanda.

Las instancias pequeñas están orientadas a ser ambientes de desarrollo que permiten hacer experimentos, testear ideas, etc.

### Amazon EC2 Modelo de Precios

![Modelo de precios](./assets/EC2Pricing.jpg)

AWS basa su modelo de precios en una combinación ideal para sus clientes de los siguientes puntos:

* *Bajo demanda:* tienes la capacidad de pagar por hora según los recursos consumidos transformando la antigua necesidad costosa de mantenimiento y actualización a un modelo más económico y optimizado.

* *Reserva de instancias:* con este modelo de precio podemos reservar maquinas de forma que se realice un pago anticipado obteniendo de esta manera un descuento significativo, usando este modelo tu puedes asegurar  un uso del 50% - 75% más bajo que la tasa bajo demanda. Este modelo es bueno para flujos de trabajo con utilidad definida.

* *Instancias puntuales:*  habilita una oferta de recursos sin utilizar de Amazon EC2 , el cual fluctuá dependiendo  de la oferta definida, esto permite un flujo de trabajo que no depende del tiempo y pueden ser interrumpidos.

* *Instancias dedicadas:* diseñadas para ejecutar instancias aisladas y dedicada a un simple cliente, generalmente se usa para ejecutar librerías de terceros.

## 2. Amazon ECS

Es el container magagment services de AWS, soporta docker container, aquí tu puedes ejecutar instancias de EC2 que soportan docker container permitiendo utilizar este servicio para manejar tus contenedores.

### Beneficios

1. Amazon ECS elimina la necesidad de instalar, operar y escalar nuestro propio  clúster.

2. Con simples llamados tenemos la capacidad de:
    * Lanzar y detener aplicaciones basadas en contenedores. 
    * Consultar el estado de tu clúster
    * Acceder  a Elastic Load Balancer, EBS Volumes  e IAM Roles.

3. Integrar tus propias políticas y librerías de terceros.

4. No adiciona carga a ECS, continuas pagando lo que uses.

## 3. AWS Lambda

AWS Lambda se puede resumir con los siguientes puntos clave: 

* Está basado en eventos los cuales pueden ser clicks del cliente o incluso otros servicios de AWS.

* No requiere manejar infraestructura de computo ni aprovisionar servidores.

* Paga por el código que usas y el tiempo que toma ejecutar

* Cero administración

## 4. Amazon Elastic Load Balancer

