# Pares de claves EC2

Una instancia EC2 utiliza una **clave pública** y una **clave privada**, estas credenciales son utilizadas para demostrar su identidad cuando se conecta a una instancia EC2. La **clave pública** se almacena en la instancia y la **clave privada** lo tendría el usuario de forma local, esta clave le permite usar **SSH** para conectar se forma segura a la instancia.

La clave pública se almacena dentro de `~/.ssh/authorized_keys`. Por región se puede tener hasta 5000 pares de claves.