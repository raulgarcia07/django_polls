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