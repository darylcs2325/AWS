# IDENTITY AND ACCESS MANAGEMENT

Es un servicio que nos permite poder administrar de forma seguro el acceso a los recursos de AWS.
Teniendo así la posibilidad de crear usuarios, accesos y permisos, agrupar a los usuarios, crear políticas para un grupo o servicio, así como roles. Todo lo anterior se conoce como identidades (usuarios, grupos y roles)

## Usuarios
Comenzamos con el **usuario raíz** quien sería el encargado de administrar todos los accesos a los recursos de AWS. Este podría identidades, siendo un usuario una identidad que podría ser una persona o aplicación.

Un usuario tiene nombre y credenciales, además de agruparlos y aplicarles políticas sobre las acciones que puede realizar, esto facilita la administración de varios usuarios.

> No se recomienda utilizar el usuario raíz para el trabajo del día a día, se aconseja crear un usuario con permisos administrativos para trabajar.

También se recomienda utilizar credenciales temporales, en lugar de crear usuarios de IAM con credenciales de largo plazo como contraseñas y claves de acceso, estos credenciales temporales se haría mediante roles

> Recomiendan proporcionar acceso a los recursos mediante las [**federación de identidades**](../definiciones/federacion%20de%20identidades.md) en lugar de crear usuarios IAM.
>
> Se evita crear crear usuarios IAM, porque tienen credenciales de largo plazo, nombre de usuario y contraseña.

Características:

- Un usuario nuevo por defecto no tiene grupo
- Tiene nombre de usuario y contraseña
- Su [ARN](../definiciones/arn.md) es: `arn:aws:iam:account-ID:user/nombre-user`
- Por defecto, no tiene permiso a realizar ninguna actividad

## Grupos

Un grupo de IAM es una identidad que especifica un conjunto de usuarios IAM. Estos grupos facilitan la administración de permisos. Por ejemplo, tenemos un grupo llamado *Administradores* y le concedemos el permiso de administrar, entonces cualquier usuario que pertenezca a ese grupo tendrá el permiso de administrar, si una nueva persona se une y tiene el cargo de administrador, entonces se le agrega al grupo o si se retira entonces se le quita del grupo.

Los grupos están relacionados con los permisos, no con la autentificación (caso de usuarios). En las  Políticas no es posible colocar a un grupo como `Principal`.

Caracterísitacas:
* Un usuario puede pertenecer a varios grupos, un grupo puede contener muchos usuarios.
* Un grupo no puede contener a otros grupos
* El número de grupos, usuarios en grupos son limitados.

## Roles

No está asociada a una persona en específica, no tiene nombre, contraseña ni clave de acceso. Se utiliza para delegar de forma temporal acceso a los recursos de AWS.

Se puede dar acceso a usuarios federados por lo que cada vez que inice sesión tendrá permisos de acuerdo al Rol. 

También para que una cuenta pueda acceder a los recursos de otra cuenta.

En caso que quiera dar acceso entre servicios, desde una instancia EC2 puede tener acceso a S3 mediante un Rol, además de poder administrar credenciales temporales

## Políticas

Es un listado de permisos que puede tener un usuario o grupo, mediante JSON se indica la acción, efecto y condición (opcional). Estos permisos puedes ser accionados a las identidades de AWS (usuarios, grupos, roles) o a recursos de AWS

### Principales tipos de políticas

* **Política basada en identidad**: Es el más común, se le asigna a las identidades de AWS.
* **Política basada en recursos**: Se asigna a los recursos de AWS, como a las políticas de bucket de S3 y políticas de confianza de roles de IAM. Se concede permiso a la entidad principal que se indica en la política.
* **Límites de permisos**: No concede permiso, sino que limita los permisos que se brindó en la Política basad en identidad

### Sintáxis


```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "1",
            "Effect": "effect",
            "Principal": {xxxx},
            "Action": "action",
            "Resource": "arn",
            "Condition": {
                "condition": {"key": "value"}
            }
        }
    ]
}
```

* ***Sid***: Es un ID para diferenciar entre las instucciones, opcional.
* **Effect**: Es el efecto que tendrá la política sobre el usuario, puede ser _Allow_ o _Deny_.
* **Principal**: Es obligatorio si se trata de una Política basada en recursos, debe indicar la identidad de AWS al que se va a permitir o denegar el acceso.
* **Action**: Es la acción específica del API del cuál se está otorgando o denegando el permiso.
* **Resource**: Obligatoria si se trata de una Política de permisos IAM, se debe incluir la lista de los recursos que se ve afectado por la acción, puede ir un [ARN](../definiciones/arn.md).
* ***Condition***: Las condiciones son opcionales, un ejemplo de su uso es establecer un periodo de uso de la política