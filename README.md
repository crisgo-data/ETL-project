![JURIDICAAÉREA ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/panel%20vuelos.jpg)


<h1 align="center"> PROYECTO ETL (EXTRACCIÓN, TRANSFORMACIÓN Y CARGA DE DATOS) </h1>


##Índice

*[ETL RETRASOS AÉREOS](#ETL-retrasos-aéreos)

*[Índice](#índice)

*[Descripción del proyecto](#descripción-del-proyecto)

*[Extracción de los datos](#Extracción-de-los-datos)

*[Limpieza y transformación de los Datos](#Limpieza-y-transformación-de-los-datos)

*[Carga de Datos a SQL](#Carga-de-datos-a-SQL)

*[Análisis y coclusión](#análisis)



<h1 align="center"> DESCRIPCIÓN DEL PROYECTO </h1>

Se trata de un proyecto en el cual se nos pide que primero extraigamos datos de tres fuentes diferentes, usando dos métodos distintos de extraccíon, en segundo lugar que hagamos una limpieza y transformación de esos datos conseguidos, y por último carguemos esos dtos a una BDD SQL. 

Este proyecto está enfocado a una empresa de que hace reclamaciones a las aerolineas por retrasos en sus vuelos con orígen o destino Madrid y Barcelona.



<h1 align="center"> Extracción de los datos </h1>

*[Primera fuente](#Primera fuente): En primer lugar, cuento con dos hojas de cálculo de excel proporcionadas por la propia compañía.

*[Segunda fuente](#Segunda fuente): 'https://www.aeropuertoinfo.com/info-sobre-vuelos/lista-de-aerolineas-en-europa/' De esta fuente he sacado mi tabla 'aerolineas' la cual me proporciona el código IATA de cada una de ellas el cual normalmente viene en el nombre del vuelo.

![tabla aerolineas ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/aerolineas.JPG)



*[Tercera fuente](#Tercera fuente): 'https://www.seguridadaerea.gob.es/es/ambitos/derechos-de-los-pasajeros/retrasos' De esta fuente saco mi cuarta tabla 'derechos'. Esta me proporciona información de los derechos de atención según la distancia del vuelo y su tiempo de retraso.

![tabla derechos ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/derechos.JPG)




<h1 align="center"> Limpieza y Transformación de los datos </h1>


- Como era de esperar la tabla proporcionada por la empresa tenía datos personales, por lo que he tenido que eliminar esas columnas y crear columnas con ID.
- También habían columnas con su 90% de datos Nulos por lo que las he eliminado.
- He añadido la columna ID-Aerolinea a la tabla reclamaciones.
- La tabla de Aerolinea solo tiene las columnas ID, nombre, código IATA y país.
- La tabla derechos cuenta con solo dos columnas.
- La dos tablas principales son las reclamaciones y las demandas. Las dos comparten columnas como sus ID.
-He eliminado Duplicados y filas con un porcentaje de 'Unknowns' de más del 60%

Al final de la transformación he pasado de 17600 filas a 16300.




<h1 align="center"> Carga de Datos a SQL </h1>


Este es el diagrama de como se relacionan las tablas entre ellas:


![Diagrama ](https://github.com/crisgo-data/ETL-project/blob/main/tablas%20SQL/imgdiagrama.PNG)

Entre las tablas reclamaciones hay una relación one to many entre ellas. 
La tabla Aerolineas tiene una relación one to many con las tablas de reclamaciones y demandas.
La tabla de derechos está al margen ya que de momento no tiene datos suficientes para poder estar relacionada con las demás tablas.



<h1 align="center"> Análisis y conclusión </h1>


Después de terminar la carga en los datos, hemos realizado las consultas, para mi más importantes, que nos aporten una información global del negocio:


1- Las tres aerolineas que mas reclamos reciben son: 
![top3 ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/aerolineasdemandas.jpg)

2- Los meses del año en que más reclamaciones hay:
![meses ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/mesreclamaciones.jpg)

3- Porcentaje de Demandas que se han cobrado:

![porcentaje ](https://github.com/crisgo-data/ETL-project/blob/main/imagenes/cobradas.jpg)



Pueden seguir añadiendose variables y columnas a esta base de datos, por ejemplo el tiempo que hizo cada uno de los días de la reclamación, o la compensación económica según la distancia del vuelo. De esa manera podríamos realizar muchas mas consultas a la BDD. 
Esto lo haré para el proyecto final.

Si teneis retrasos en los vuelos mayores a un par de horas, con orígen o destino Madrid o Barcelona os dejo en enlace a la web de #LegalSky
https://legalsky.es/





