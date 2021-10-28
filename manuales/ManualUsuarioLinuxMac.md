# Manual de instalacion PAVI Back-End

## Requisitos:
* git 2.30.2 
* python 3.8.11 (**IMPORTANTE**: Incluir en la instalacion el comando "pip")
* Postman (Opcional)

> probado en fedora 33 y 34

### paso 1: clonar el repositorio
1.1.- Abrir la terminal.\
1.2.- Explorar las carpetas hasta llegar a la carpeta donde se desea clonar el repositorio.\
1.3.- escribimos el comando `git clone https://github.com/HectorCosgalla/PAVI_api` y esperamos a que termine.

### paso 2: instalamos un entorno virtual
2.1.- Accedemos a la carpeta del repositorio clonado.\
2.2.- Ejecutamos el comando `python3.8 -m venv venv/` y esperamos a que termine (**IMPORTANTE**: En caso de tener mas de una version de python instalada, es primordial que cada que se quiera ejecutar algun comando de python sea con python3.8, pues es la ultima version compatible con las demas dependencias).


### paso 3: instalar los requerimientos de ambiente
3.1.- Ejecutamos el entorno virtual con `source venv/bin/activate`\
3.2.- Ejecutamos el comando `pip install -r requirements-dev.txt`

### paso 4: Ejecutamos la app
4.1.- Primero creamos un archivo con el nombre `.env` y lo guardamos en la carpeta principal (Donde se encuentra el archivo run.py) con el siguiente contenido:
```
DB_USER = admin-pavi
DB_PASSWORD = paviPassword
DB_HOST = pavi.eywsg.azure.mongodb.net
DB_NAME = pavi
DB_COLLECTION = videos

FLASK_ENV = development
FLASK_RUN_PORT = 5000
```
**Paso opcional (En caso de querer ver como se procesa el video):** Abrir el archivo "yolov4" que se encuentra en la direccion "~/pavi/pavi/services" y en la ultima linea borrar la parte que dice `, no_show=True`\
4.2.- Ejecutamos la app con el comando `python3.8 run.py`

## Uso de la API
### Procesando el video.
1. Abrimos el navegador en la pagina `http://localhost:5000/documented_api/doc`
2. Hacemos click en la pestaña que dice **videos** *Video processing endpoint*
3. Seleccionamos la pestaña **POST** e inmediatamente en el boton **Try it out**
4. En la seccion de **video** seleccionamos el video que deseanos procesar
5. En la seccion **algorithm** no cambiamos nada
6. Presionamos **Execute** y esperamos a que termine de procesar el video.

### Obteniendo Los resultados
1. Abrimos el navegador en la pagina `http://localhost:5000/documented_api/doc`\
2. Hacemos click en la pestaña que dice **videos** *Video processing endpoint*
3. Seleccionamos la pestaña **GET** e inmediatamente en el boton **Try it out**
4. En la seccion de **video_id** escribimos en nombre de un video existente en la base de datos (Por ejemplo: Run).
5. Presionamos **Execute** y esperamos a que tener la lista de resultados.



## Posibles errores:
1.- Error "gcc: error fatal: cannot execute ‘cc1plus’: execvp: No existe el fichero o el directorio"\
**Solucion**: Instalar el paquete gcc-g++ con el comando `sudo dnf install gcc-g++`
