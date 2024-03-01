# Fundamentos básicos de cURL

Client URL (cURL) es una herramienta de línea de comando utilizada para transferir datos desde o hacia un servidor, utilizando varios protocolos como HTTP, HTTPS, FTP, FTPS, SCP, SFTP.

## Comandos básicos

Debemos tener en cuenta que cada vez que queramos GET, POST, PUT, DELETE debemos colocar `-X` seguido de la solicitud que queremos usar, `curl -X GET ...` pero no siempre es obligatorio ya en muchos casos cURL puede inferir automáticamente el método HTTP. Por ejemplo:

* Si se utiliza `-d`, se infiere que se trata de un `POST`.
* Si no se utiliza nada, y solo se ejecuta `curl http://example.com`, cURL realizará un petición `GET`.
* Si utiliza `-o` o `-O` para descargar un archivo, cURL lo tomará como una petición `GET`


**Solicitud GET**

`curl http://example.com`

**Solicitud POST**

`curl -X POST -d "key=value&key2=value2" http://example.com`

O podemos usar también

`curl -d "key=value&key2=value2" http://example.com`

**Solicitud PUT**

`curl -X PUT -d "title=Mi primer PUT&body=Este es el nuevo cuerpo" http://example.com/1` En este caso estamos actualizando el item 1 

**Solicitud DELETE**

`curl -X DELETE http://example.com/1` Estamos eliminando el item 1

**Descargar archivo**

`curl -o nombre-archivo.xx http://example.com`

Si no queremos ingresar un nombre de archivo, podemos hacerlo con `-O`

`curl -O http://example.com`

**Formato personalizado de salida**

Si queremos especificar un formato de salida de la información de una solicitud HTTP, escribiendo `--write-out`. Podemos ver el código de estado HTTP de la respuesta con `--write-out "%{http_code}"` o el tiempo total de la solicitud `--write-out "%{time_total}"`

`curl --write-out "HTTP code: %{http_code}\nTotal time: &{time_total}\n" -o /dev/null -s http:example.com`

En este caso, estamos obteniendo el estado de la respuesta y el tiempo total de la solicitud, `-o /dev/null` estamos redirigiendo la salida a `/dev/null`, este último se utiliza para descartar datos; es decir, todo lo que se envíe a `/dev/null` se "elimina" sin ser almacenado en ningún lugar, si no ponemos esto en la consola nos arrojaría todo el contenido que no nos interesa.
`-s` es la abreviatura de `--silent` sirve para silenciar la salida de progreso; es decir, no nos saldría en la consola la tabla de la descarga.

