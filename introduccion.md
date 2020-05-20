# ¿Qué es el cloud computing

Conocida también como servicios en la nube, es la posibilidad de ofrecer diversos servicios mediante internet.

Esta cuenta con varias ventajas y que son las que constituyen la potencia del Cloud Computing:

1. On-demand
2. IT resources
3. Accesible online
4. Pay-as-you-go

# AWS History and Global Reach

Cerca de un millón de clientes en más de 190 países 

AWS provee servicios para todo tipo de industrias ya sea una empresa, Startups o al sector público, entre las que sus cifras rondan:
* Cerca de 2,000 agencias gubernamentales
* 5,000 instituciones académicas
* 7,500 organizaciones sin ánimo de lucro

AWS continuamente está creciendo y mejorando al lanzar desde 2017 1,430 características nuevas.

# Comparando AWS con las arquitecturas tradicionales

# Entendiendo las regiones

###  Que es una región

Una región es un área geográfica con dos o más zonas de disponibilidad.

### Saber escoger la región puede afectar en:

* Optimización de latencia
* Optimización de costos
* Requerimientos regulatorios

### Entidades completamente separadas

Las regiones son independientes las unas de las otras.

### Comunicación entre regiones 

Esto ocurre sobre internet público donde la data es encriptada en su transito.

## Zonas de disponibilidad

Una zona de disponibilidad es una colección de data center en una región, cada uno es aislado de otras zonas de disponibilidad y es conectado para velocidad y baja latencia.

Aislar las zonas de disponibilidad  protegen de cada una de las fallas a las demás zonas de disponibilidad.

Adicionalmente la baja latencia hace que sea posible que una zona de disponibilidad se comunique con otra de forma que se puedan hacer peticiones de recursos entre ellas.Por esta razón una buena practica es provisionar recursos en múltiples zonas de disponibilidad.

## Edge Locations 

AWS edge locations sirve como host para content delivery network (CDN), lo que se conoce como CloudFront. Amazon Cloud front puede ser usado para desarrollar sitios web y contenido que es dinámico, estático o transmitido. Las peticiones de contenido son automáticamente enrutados a la edge location más cerca para aumentar la velocidad de transmisián del contenido para los clientes.

Por ejemplo, si desplegamos un nuevo sitio web en una región de AWS que este cerca de tu localización, como buena práctica tu podrías usar múltiples zonas  para protegerte de interrupciones de servicio y también permitir que tus usuarios carguen mas rápido el contenido donde lo estén usando.