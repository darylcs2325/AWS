# Grupo de Seguridad

Un grupo de seguridad es como un firewall virtual para controlar el tráfico entrante y saliente. Se indica reglas, tanto para las entradas como para las salidas.

Permite especificar qué protocolos (HTTP, HTTPS, SSH, ...), puertos y los IP que pueden acceder a las instancias.

**Puertos importantes**

* **22**: *SSH* (Secure Shell)- Logear en instancias Linux
* **21**: *FTP* (File Transfer Protocol) - Subir archivos compartidos
* **22**: *SFTP* (Secure File Transfer Protocol) - Subir archivos con SSH
* **80**: *HTTP* - Acceso a webs sin seguridad
* **443**: *HTTPS* - Acceso a webs seguras
* **3389**: *RDP* (Remote Desktop Protocol) - Logear en una instancia Windows

## Reglas de seguridad
Las reglas de seguridad controlan el tra´fico entrante que puede llegar a las instancias asociadas al grupo de seguridad.

Características importantes:

* EC2 bloquea el tráfico del puerto 25 de forma predeterminada.
* Las reglas de seguridad son permisivas; no puede crear reglas que denieguen acceso.
* El envío de solicitud desde una instancia es registrada por el grupo de seguridad y esta automáticamente permite el ingreso de la respuesta de la solicitud. Lo mismo para el VPC, la instancia recibe la respuesta de una solicitud saliente (e.g. respuesta del servidor web a una petición realizada), el flujo de salida de esta respuesta está automáticamente permitido, sin importar las reglas de salida configuradas en el grupo de seguridad.
* Puede agregar y eliminar reglas en cualquier momento. Los cambios se aplican automáticamente a las instancias que estén asociadas al grupo de seguridad.
* Una instancia puede tener uno o más grupos de seguridad.