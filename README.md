# Bienvenidos a la librería de encuestas de django

A continuación vamos explicar como instalar el proyecto.

1. Descargar el repositorio con el código con el siguiente comando:

```
git clone https://github.com/raulgarcia07/django_polls.git
```

2. Entramos en la carpeta `djangopolls` y crear el entorno virtual con el comando:
```
python -m venv .venv 
o
python3 m venv .venv 
```
3. Activar el entorno virtual con el comando:
```
source .venv/bin/activate for Linux

\path\to\env\Scripts\activate for Windows
```
4. Activar las librerias necesarias para este proyecto que se encuentra en el fichero `requirements.txt` con el comando:
```
pip instal -r requirements.txt
```

5. Ejecutamos las migraciones iniciales

```
python manage.py migrate
```

6. Cargamos los datos iniciales con:

```
python manage.py loaddata fixtures/polls_data.json
```

7. Configuramos el archivo `django_polls/settings.py` , añadiendo la dirreción de loopback `127.0.0.1 ` (en la linea 28) de forma que en la linea aparezca al menos esa dirreción ip:

```
ALLOWED_HOSTS = ['192.168.33.10', '127.0.0.1']
```

8. Arrancar el servidor con:
```
python manage.py runserver
```

## Despliegue de la aplicación eb varias máquinas

1. Instalar fabric en el entorno virtual con el comando:
```
pip install fabric
```

2. Cambiar los datos de acceso a la máquina remota, localizados en la función ´development(ctx)´ del archivo fabfile.py ,líneas 12-16:

```
@task
def development(ctx):
    ctx.user = 'vagrant'
    ctx.host = '192.168.33.10'
    ctx.connect_kwargs = {"password": "vagrant"}
 ``` 

 3. Ejecutar el script con el comando:

 ```
 fab development deploy
```

4. Se pueden añadir varios entornos de configuración creando funciones del tipos del paso 2:
```
@task
def production(ctx):
    ctx.user = 'vagrant'
    ctx.host = '192.168.33.10'
    ctx.connect_kwargs = {"password": "production"}
 ``` 

 5. Y ejecutar el script con el comando con la estructura `fab nombre-de-la-función`, en este caso:
    ```
    fab production deploy
    ```