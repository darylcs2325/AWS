# Amazon Resource Name

Sirve para identificar de forma exclusiva los recursos de AWS, esto lo realiza de manera inequívoca.

Formato:

`arn:partition:service:region:account-id:resource-id`
* partition: Indica la partición de AWS que se utiliza, pueden ser:
	* aws: Partición estándar de AWS
	* aws-cn: Partición de AWS China
	* aws-us-gov: Partición del gobierno de EE.UU.
* service: Indica el servicio al que pertenece el recurso, puede ser ec2, s3, iam, etc.
* region: Indica la región geográfica el cuál se encuentra el recurso.
* account-id: Es el ID de la cuenta de AWS propietaria del recurso.
* resource: Identifica el recurso específica dentro del servicio.

Ejemplo:

**Usuarios de IAM**

`arn:aws:iam::12345678123:user/ivan`

**Bucket de S3**

`arn:aws:s3:::nombre_bucket`

## Uso de caracteres comodines en rutas

Se utiliza el `*` como indicador de todo, ejemplos:

`arn:aws:iam::123456789012:user/Development/product_1234/*`

*Esto indica que del usuario `Development` del producto `product_1234` queremos todo lo que está asociado*

`arn:aws:iam::123456789012:user/*` *todos los usuarios*

`arn:aws:iam::123456789012:group/*` *todos los grupos*