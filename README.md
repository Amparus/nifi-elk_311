![enter image description here](https://n3m5z7t4.rocketcdn.me/wp-content/plugins/edem-shortcodes/public/img/logo-Edem.png)



# Ejercicio Nifi  ELK 

Usando nifi+ELK hay que presentar una solución que muestre sobre un mapa la disposición de delitos presentes en esta api:


## API
https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

	JSON
	https://data.cityofnewyork.us/resource/erm2-nwe9.json

## NIFI
http://localhost:8080/nifi/?processGroupId=root&componentIds=e6258f27-0176-1000-857a-fcd85cd1a73a


## KIBANA
http://localhost:5601/app/kibana#/dev_tools/console?_g=()



### 1. Levantar contenedores en DOCKER que permitan acceder a las distintas aplicaciones. Agrego al docker de Roberto, los contenedores de NIFI de la clase de Esteban. 

### 2. Acceder a NIFI, para crear la estructura que permita extraer la información de la API facilitada. 
	2.1 Añadir y configurar procesadores
		InvokeHTTP: con la URL de la API https://data.cityofnewyork.us/resource/erm2-nwe9.json
		SplitJson: Convertirá la información de la URL en JSON, lenguaje que necesitará Elastic para ser interpretado
		PutElasticSearchHTTP: Llevará la información a ElasticSearch
	2.2 Comprobar que no hay errores

### 3. Acceder a Kibana, para crear el esquema que permita el acceso de la información del JSON y transformarla para que pueda ser visualizada en un mapa. Para ello, hay que reindexar los puntos de localización y transformarlos en GEO_POINT. 
	3.1 DEV TOOLS, para crear el esquema y configurar el campo de localizacion de STRING en GEO_POINT. -PLAY- Generará los ficheros o índices en 
	3.2 MANAMENT 
		3.2.1 INDEX MANAGEMENTS. Comprobar que los ficheros se han generado. Revisar que el campo 'location' está en formato GEO_POINT
		3.2.2 INDEX PATTERN. Generar patrón con el nuevo fichero recodificado: 'new_crime'
	3.3 MAPS Add Layer con el patrón generado y visualizar. :)
	3.4 DASHBOARD. Generar pizarra, con el tipo mapa de coordenadas y con resumen del fichero con los campos más relevantes o que requieran ser comentados. 

	


----------------------------------------------------------------------------------------------------------
[24/12/20 10:06] Nieto Pelaez, Pedro (Invitado) said
    Hola Máster en Data Analytics 20-21 perdonad por el retraso: Aquí tenéis el entregable de Nifi + ELK:

El ejercicio a realizar es:
Usando nifi+ELK debéis presentar una solución que muestre sobre un mapa la disposición de delitos presentes en esta api:

https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

Entregables:
	Enlace a código Github
	Captura de pantalla de vuestra interfaz Kibana

Opcional:
Existen otras fuentes de datos que proporcionan también llamadas al 311 de otras zonas, opcionalmente podéis concatenar más datasets y pintarlos de manera conjunta.
	https://catalog.data.gov/dataset/311-data-in-development


Debido a mi memoria, ampliamos una semana el entregable (16 Enero), aprovechad durante las navidades!!!
