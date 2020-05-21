# AWS Storage & Content Delivery

## Servicios

1. Amazon Simple Storage Service (S3)

    ## Casos de uso

    * Almacenamiento de recursos de aplicación (Assets)
    * Sitios Web estáticos
    * Backup
    * Stagin area para Big Data

2. Amazon Elastic Block Store

3. Amazon CloudFront

 Es un servicio de AWS orientado a ofrecernos la posibilidad de almacenar nuestros recursos en edge locations dependiendo del lugar de demanda, brindando tiempos de latencia menor a los usuarios al ofrecernos la capacidad de crear Content Delivery Networks(CDN).

### Acerca de CloudFront

* red de crecimiento global
* Contenido seguro a la mano
* Integración profunda clave con los servicios AWS
* Alto rendimiento
* Económico
* Fácil de usar

### Casos de uso 

* Cacheo de recursos estáticos
* Transmisiones de video bajo demanda
* Seguridad y protección a ataques DDoS
* Personalizar y dinamizar contenido 
* Acelaración API
* Distribución de software

CloudFront también nos ayuda a dar bastante disponibilidad puesto que al exponer estos recursos en edge locations, si algo llegase a pasar con nuestro servidor, cloudfront seguira mostrando los recursos sin importar si esta caido el servicio.

4. AWS Data Pipeline

Es un web service que nos ayuda a mover data entre un servicio u otro. 

### Componentes del pipeline

* DataSource 
    son la fuente de la información que sera movida entre los servicios deseados (Dynamodb, etc...)
* Activities 
    Estas definen las acciones a ser ejecutadas como queries
* Schedule 
    define el tiempo en el que se activara  las tareas
* Preconditions
    Son aquellas que determinan cuando deben ejecutarse las tareas segun unas condiciones especificas 

### Compatibilidad AWS Services

AWS Data Pipeline es compatible con los siguientes servicios de computo:
* Amazon EC2
* Amazon EMR 

Tambien es compatible con los siguientes servicios de almacenamiento:

* Amazon S3
* Amazon RDS
* Amazon DynamoDb
* Amazon Redshift 

Cabe decir que AWS Data Pipeline tambien es compatible con onpremise jdbc database.


### Casos de uso

* Operaciones de Extraer, transformar y cargar data
* backups base de datos
* Amazon EMR jobs
* Importando data

### Beneficios

* Confiable
* facil de usar 
* flexible
* Escalable

5. AWS Snowball Edge