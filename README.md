# Jupyter Lab Stack

Este repositorio contiene un stack para **docker-compose** que pone en marcha Jupyter Lab, servido con SSL a través de Nginx.

## Puesta en marcha

Para iniciar el proyecto es necesario hacer dos cosas:

* Ajustar las variables de entorno
* Proporcionar un certificado SSL

### Ajuste de variables de entorno

Se proporcionarán mediante un fichero ``.env``. Para ello, hay que copiar el fichero de ejemplo ``.env.example`` y escribir ahí la configuración deseada:

```
cp .env.example .env
```

Para editarlo:

```
nano .env
``` 

En el fichero se indicarán una clave o token de acceso y la ruta de la carpeta que será tratada como alojamiento de los trabajos del usuario, típicamente el ``$HOME`` de un usuario.


### Generación de un certificado SSL autofirmado (opcional)

Si no se dispone de un certificado SSL, puede generarse uno autofirmado. Téngase en cuenta que este tipo de certificados suponen una brecha de seguridad si no se verifica su origen; no obstante, en entornos de confianza, son perfectamente válidos en cuanto se confima la excepción de seguridad en el navegador.

Para generar uno de estos certificados, utilícese el siguiente comando:

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ssl.key -out ssl.pem
```


### Lanzamiento del stack

Desde la misma carpeta de este proyecto, lanzar el comando siguiente:

```
docker-composer up -d
```


### Interrupción del servicio

Utilícese este otro comando:

```
docker-composer down
```


## Acceso al servicio

Desde un navegador, introducir el URL ``https://servidor/``, reemplazando _servidor_ por la dirección IP o nombre de dominio del servidor donde se haya lanzado el stack.

La primera vez, nos solicitará un token de acceso. Introduciremos aquí la clave que hayamos configurado en las variables de entorno.

