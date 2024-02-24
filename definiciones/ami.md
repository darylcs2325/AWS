# Instancias y AMI

Amazon Machine Image (AMI) son utilizadas para crear máquinas virtuales dentro de AWS, esta plantilla contiene toda la información necesaria para lanzar una instancia EC2 tales como: sistema operativo, software de aplicación, configuraciones de red y datos relacionados; es la imagen con que se crea las máquinas virtuales como en VirtualBox o VMware. Además, indicaremos las demás características como CPU, memoria, almacenamiento, red, grupo de seguridad, entre otros ([tipo de instancia](../definiciones/tipo-instancia.md)) para tener nuestra máquina virtual completa.

Cuando se lanza una instancia, se crea un **volumén raíz** para dicha instancia. Este contiene la imagen que se usa para arrancar dicha instancia. Hay dos tipos de volumen raíz, uno es `ebs` (respaldada por Amazon EBS) y otra `instance store` (respaldo por almacen de instancias). El **EBS** tiene la características de ser un almacenamiento persistente, es decir, aún cuando la instancia se detenga, lo que está en el volumen no se pierde y es más rápido el tiempo de arranque, solo se elimina cuando se da *terminar instancia*. El **Instance Store** los datos en cualquier volumen de instancia se conserva solo durante el ciclo de vida de la instancia y el tiempo de arranque es menor a 5 min.

## Pasos para lanzar una instancia

