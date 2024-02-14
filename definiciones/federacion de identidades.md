# Proveedor de Identidades Federadas (IdP)

Es un método que permite a los usuarios autentificarse, en este caso a los servicios de AWS. En lugar de usar credenciales de AWS, esto se logra al establecer una relación entre AWS y IdP.
Algunos ejemplos de estos son:
- PingID
- Azure AD
- Okta

> Cualquier IdP que soporte SAML 2.0 será compatible con AWS.

Este tipo de herramientas no solo nos permitirá poder acceder a los servicios de AWS, sino que también a herramientas externas, como Jira, solo con un usuario del IdP. De esta forma, tendremos centrado todos los usuarios de la compañía y reduciendo el uso de usuarios IAM.