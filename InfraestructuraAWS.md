# AWS Infraestructura Global

## AZs 

* Un único centro de datos típico alberga varios miles de servidores
* Todos los centros de datos están en línea
  * Ningún centro de datos está en modo "cold", esto quiere decir que ningún centro se encuentra en modo pasivo, lo que significa que todos los centros de datos reciben peticiones del cliente, lo que permite que en caso de falla todo el tráfico sea redirigido de forma que siempre se equilibre los datos entre los disponibles.

Se conoce como AZs (Availability zones) como las zonas de disponibilidad de AWS

* Cada zona de disponibilidad está: 
  * Compuesta de uno o más centros  de datos
    *  Existen zonas que incluyen hasta 6 centros de datos
    * Ningún centro de datos puede ser parte de varias zonas de disponibilidad
  * Diseñada para el aislamiento de fallas
  * Interconectada con otras AZs mediante enlaces privados de alta velocidad 

![ 				Regiones y zonas de disponibilidad 			](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/images/aws_regions.png)

La imagen representa que cada región es totalmente independiente, cada zona de disponibilidad está aislada pero dichas zonas están conectadas  a través de conexiones de baja latencia. En el siguiente diagrama se ilustra la relación entre las regiones y las zonas de disponibilidad. Hay que tener en cuenta que AWS nunca sacará tus datos de una región es responsabilidad del cliente replicar datos en todas las regiones si así lo requieren las necesidades de tu negocio. AWS proporciona información sobre el país y, en su caso, el estado donde reside cada región. Tú eres responsable de seleccionar la región para almacenar datos en función de tus necesidades y los requisitos de latencia de la red.

Según la página oficial de AWS Amazon EC2 está hospedado en varias ubicaciones de todo el mundo. Dichas ubicaciones se componen de regiones y zonas de disponibilidad. Cada *región* es un área geográfica independiente. Cada región tiene varias ubicaciones aisladas conocidas como *zonas de disponibilidad*. Amazon EC2 ofrece la posibilidad de colocar recursos, como instancias y datos, en varias ubicaciones. Los recursos no se replican en las regiones, a menos que usted decida hacerlo específicamente.

Amazon opera centros de datos de alta disponibilidad con tecnología de vanguardia. Aunque es infrecuente, puede suceder que se produzcan errores que afecten a la disponibilidad de las instancias que están en la misma ubicación. Si hospeda todas las instancias en una misma ubicación y allí se produce un error, ninguna de las instancias estaría disponible.

Ubicaciones de los recursos

Algunos recursos se pueden usar en todas las regiones (globales) y otros son específicos de la región o la zona de disponibilidad en la que se residen.

| Recurso                                           | Tipo                   | Descripción                                                  |
| :------------------------------------------------ | :--------------------- | :----------------------------------------------------------- |
| Cuenta de AWS                                     | Global                 | Puede usar la misma cuenta de AWS en todas las regiones.     |
| Pares de claves                                   | Global o regional      | El par de claves que crea con Amazon EC2 están vinculadas a la región en la que se crean. Puede crear un par de claves RSA propio y cargarlo en la región en la que desea usarlo; por tanto, puede hacer que el par de claves esté globalmente disponible cargándolo en cada región.Para obtener más información, consulte [Pares de claves de Amazon EC2](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/ec2-key-pairs.html). |
| Identificadores de recursos de Amazon EC2         | Regional               | Cada identificador de recurso, como un ID de AMI, de instancia, de volumen de EBS o de instantánea de EBS, está vinculado a su región y solo puede usarse en la región en la que fue creado. |
| Nombres de recursos proporcionados por el usuario | Regional               | Cada nombre de recurso, como un nombre de grupo de seguridad o un nombre de par de claves, está vinculado a su región y solo puede usarse en la región en la que fue creado. Aunque puede crear recursos con el mismo nombre en varias regiones, no están relacionado entre ellos. |
| AMI                                               | Regional               | Una AMI está vinculada a la región donde se encuentran los archivos dentro de Amazon S3. Puede copiar una AMI de una región en otra. Para obtener más información, consulte [Copiar una AMI](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/CopyingAMIs.html). |
| Direcciones IP elásticas                          | Regional               | Una dirección IP elástica está vinculada a una región y solo puede asociarse a una instancia que esté en la misma región. |
| Grupos de seguridad                               | Regional               | Un grupo de seguridad está vinculado a una región y solo puede asociarse a una instancia de la misma región. No puede habilitar una instancia para comunicarse con una instancia fuera de su región por medio de reglas de grupo de seguridad. El tráfico desde una instancia de otra región se considera ancho de banda WAN. |
| Instantáneas de EBS                               | Regional               | Una instantánea de EBS está vinculada a su región y solo puede utilizarse para crear volúmenes en la misma región. Puede copiar una instantánea de una región a otra. Para obtener más información, consulte [Copia de una instantánea de Amazon EBS](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/ebs-copy-snapshot.html). |
| Volúmenes de EBS                                  | Zona de disponibilidad | Los volúmenes de Amazon EBS están vinculados a una zona de disponibilidad y solo se pueden adjuntar a instancias de esa misma zona de disponibilidad. |
| Instancias                                        | Zona de disponibilidad | Una instancia está vinculada a la zona de disponibilidad en la que se lanzó. Ahora bien, su ID de instancia está vinculado a la región. |

### Regiones

Cada región de Amazon EC2 se ha diseñado para que esté totalmente aislada de las demás regiones de Amazon EC2. Con ello se consigue la mejor tolerancia a errores y estabilidad posibles.

Cuando vea sus recursos, solo verá los que estén vinculados a la región especificada. Esto se debe a que las regiones están aisladas entre sí y no replicamos automáticamente los recursos en distintas regiones.

Cuando lanza una instancia, debe seleccionar una AMI que esté en la misma región. Si la AMI está en otra región, puede copiar la AMI a la región que está usando. Para obtener más información, consulte [Copiar una AMI](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/CopyingAMIs.html).

Tenga en cuenta que existe un cargo por transferencia de datos entre regiones. Para obtener más información, consulte [Precios de Amazon EC2: transferencia de datos](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer).

### Zonas de disponibilidad

Cuando lanza una instancia, puede seleccionar una zona de disponibilidad o dejar que elija una por usted. Si distribuye las instancias entre varias zonas de disponibilidad y una de las instancias genera un error, puede diseñar la aplicación de forma que una instancia en otra zona de disponibilidad pueda gestionar las solicitudes.

También puede usar direcciones IP elásticas para enmascarar los errores de una instancia en una zona de disponibilidad, volviendo a mapear rápidamente la dirección hacia una instancia en otra zona de disponibilidad. Para obtener más información, consulte [Direcciones IP elásticas](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html).

Una zona de disponibilidad está representada por un código de región seguido de un identificador de letra; por ejemplo, `us-east-1a`. Para garantizar que los recursos se distribuyen por todas las zonas de disponibilidad de una región, asignamos zonas de disponibilidad de manera independiente a el nombre de cada cuenta de AWS. Por ejemplo, es posible que la zona de disponibilidad `us-east-1a` de su cuenta de AWS no se encuentre en la misma ubicación de `us-east-1a` que otra cuenta de AWS.

Para coordinar las zonas de disponibilidad entre cuentas, debe usar el *ID de AZ*, que es un identificador único y constante de una zona de disponibilidad. Por ejemplo, `use1-az1`es un ID de zona de disponibilidad para la región `us-east-1` y tiene la misma ubicación en cada cuenta de AWS.

La visualización de los ID de zona de disponibilidad le permite determinar la ubicación de los recursos de una cuenta en relación con los recursos de otra cuenta. Por ejemplo, si comparte una subred en la zona de disponibilidad con el ID de zona de disponibilidad `use-az2` con otra cuenta, esta subred se encuentra disponible para esa cuenta en la zona de disponibilidad cuyo ID de zona de disponibilidad es también `use-az2`. El ID de zona de disponibilidad para cada VPC y subred aparece en la consola de Amazon VPC. Para obtener más información, consulte la sección sobre el [uso compartido de VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html) en la *Guía del usuario de Amazon VPC*.

A medida que las zonas de disponibilidad crecen a lo largo del tiempo, nuestra capacidad de ampliarlas podría verse limitada. Si esto sucediera, podríamos restringir el lanzamiento de instancias en una zona de disponibilidad limitada a menos que ya tuviera una instancia en dicha zona de disponibilidad. Con el tiempo, también podríamos quitar la zona de disponibilidad limitada de la lista de zonas de disponibilidad de las nuevas cuentas. Por consiguiente, una cuenta podría tener un número diferente de zonas de disponibilidad disponibles en una región que otra cuenta.

## Servicios gestionados vs no gestionados

Los servicios de AWS se clasifican en dos tipos:

* Servicios no gestionados
   * El escalado
   * La tolerancia a fallas y  la disponibilidad son administrados por usted

No están incorporados en el servicio, lo que requiere configuración adicional y administración por parte del servicio. Básicamente los servicios no gestionados se aprovisionan por el usuario sin ninguna configuración inicial de alta disponibilidad. Los servicios no gestionados requieren que **el usuario administre la forma en que los servicios responden a los cambios en la carga, los errores y las situaciones en que los recursos no están disponibles.** 

Por ejemplo, si ejecutas un servidor web en una instancia de [Amazon EC2](https://www.josemariagonzalez.es/amazon-web-services-aws/que-es-amazon-elastic-compute-cloud-amazon-ec2.html), ese servidor web no se escalará para manejar una mayor carga de tráfico o reemplazar instancias no saludables por otras sanas **a menos que especifique una solución de escalado como “Auto Scaling”, porque Amazon EC2 es una solución no administrada.**

* Servicios gestionados
  * La escala 
  * La tolerancia a fallas 
  * disponibilidad  

Están incorporados por el servicio. Si tienes un sitio web estático que está alojando una solución de almacenamiento basada en la nube como [Amazon S3](https://www.josemariagonzalez.es/amazon-web-services-aws/como-crear-un-servidor-web-en-amazon-s3.html) sin un servidor web, **esas características de escalado, tolerancia a fallas y disponibilidad serían manejadas internamente por Amazon S3, porque S3 si es una solución administrada**.

Los servicios gestionados aún requieren que el usuario los configure, por ejemplo, crear un cubo de Amazon S3 y establecer permisos para él. Sin embargo, los **servicios gestionados generalmente requieren menos configuración**.

En conclusión a todo lo anterior el beneficio de usar un servicio no gestionado, **es que tienes más control  del servicio o aplicación**

## Modelo de responsabilidad compartida AWS

Los asuntos relacionados con la seguridad y la conformidad son una responsabilidad compartida entre AWS y el cliente. Este modelo compartido puede aliviar la carga operativa del cliente, ya que AWS opera, administra y controla los componentes del sistema operativo host y la capa de virtualización hasta la seguridad física de las instalaciones en las que funcionan los servicios. El cliente asume la responsabilidad y la administración del sistema operativo invitado (incluidas las actualizaciones y los parches de seguridad), de cualquier otro software de aplicaciones asociado y de la configuración del firewall del grupo de seguridad que ofrece AWS. Los clientes deben pensar detenidamente en los servicios que eligen, ya que las responsabilidades varían en función de los servicios que utilicen, de la integración de estos en su entorno de TI y de la legislación y los reglamentos correspondientes. La naturaleza de esta responsabilidad compartida también ofrece la flexibilidad y el control por parte del cliente que permite concretar la implementación. Como se muestra a continuación, la diferenciación de responsabilidades se conoce normalmente como seguridad "de" la nube y seguridad "en" la nube.

**Responsabilidad de AWS en relación con la "seguridad de la nube":** AWS es responsable de proteger la infraestructura que ejecuta todos los servicios provistos en la nube de AWS. Esta infraestructura está conformada por el hardware, el software, las redes y las instalaciones que ejecutan los servicios de la nube de AWS.

**Responsabilidad del cliente en relación con la "seguridad en la nube":** la responsabilidad del cliente estará determinada por los servicios de la nube de AWS que el cliente seleccione. Esto determina el alcance del trabajo de configuración a cargo del cliente como parte de sus responsabilidades de seguridad. Por ejemplo, un servicio como Amazon Elastic Compute Cloud (Amazon EC2) se clasifica como Infraestructura como servicio (IaaS) y, como tal, requiere que el cliente realice todas las tareas de administración y configuración de seguridad necesarias. Los clientes que implementan una instancia de Amazon EC2 son responsables de la administración del sistema operativo huésped (incluidos los parches de seguridad y las actualizaciones), de cualquier utilidad o software de aplicaciones que el cliente haya instalado en las instancias y de la configuración del firewall provisto por AWS (llamado grupo de seguridad) en cada instancia. En el caso de los servicios extraídos, como Amazon S3 y Amazon DynamoDB, AWS maneja la capa de infraestructura, el sistema operativo y las plataformas, mientras que los clientes acceden a los puntos de enlace para recuperar y almacenar los datos. Los clientes son responsables de administrar sus datos (incluidas las opciones de cifrado), clasificar sus recursos y utilizar las herramientas de IAM para solicitar los permisos correspondientes.

![Shared_Responsibility_Model_V2](https://d1.awsstatic.com/security-center/Shared_Responsibility_Model_V2.59d1eccec334b366627e9295b304202faf7b899b.jpg)

Este modelo de responsabilidad compartida entre los clientes y AWS también abarca los controles de TI. De la misma forma que AWS y sus clientes comparten la responsabilidad del funcionamiento del entorno de TI, también comparten la administración, el funcionamiento y la verificación de los controles de TI. AWS puede ayudar a aliviar la carga que supone para los clientes operar los controles, para lo que administra los controles asociados con la infraestructura física implementada en el entorno de AWS de cuya administración se encargaba anteriormente el cliente. Dado que la implementación de cada cliente se realiza de manera diferente en AWS, los clientes tienen la oportunidad de migrar a AWS la administración de determinados controles de TI para obtener un (nuevo) entorno de control distribuido. Los clientes pueden usar la documentación de conformidad y control de AWS disponible para ejecutar sus procedimientos de verificación y evaluación de controles según sea necesario.

Recursos

* <https://www.josemariagonzalez.es/amazon-web-services-aws/infraestructura-global-de-amazon-aws.html>
* <https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-regions-availability-zones>
* <https://aws.amazon.com/es/compliance/shared-responsibility-model/>