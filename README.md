# Proyect_1_MLOps
## Proyecto Individual n°1 MLOps: Sistema de recomendación de peliculas

Este proyecto, es el primero de 2 proyectos de Lab´s, donde asumo el rol de un ingeniero de datos, que se le ha encargado, la tarea de transformar datos crudos y sin procesar, con la cual desarrollare un sistema de recomendación funcional.

# Objetivo del proyecto
Cumplir con la misión que nuestro cliente nos encargo, nuestro cliente  ofrece servicios de agregación de plataformas de streaming. Los datos que se nos han sido entregados, estan en un estado bastante complicado, estan anidados,desordenados y con
valores faltantes y nulos. Con estos datos debemos entregar un MVP (Producto Mínimo Viable) que sea funcional y eficaz en un tiempo muy limitado.

### Resultado a entregar 
Un sistema de recomendación que satisfaga al cliente y ademas se pueda mejorar en el futuro, agregando mas funciones, de tal manera que sea un producto escalable.

# Desarrollo 
Los 2 archivos csv, contenian aproximadamente 45,000 filas de datos sin procesar. Estos datos deben de ser limpiados de tal manera, que las 6 funciones claves a desarrollar (a petición del cliente) puedan consumir estos datos. 
Tras completar estas 6 funciones, estas mismas se implementaran a traves de una API que sera desplegada en RENDER, para su accesibilidad y facilidad de uso.

# Proceso de Etl
En la carpeta de ETL, se encuentran los notebooks dedicados al ETL (Extracción,Transformación y Carga), donde see da una detallada los procesos que se usaron para limpiar los datos.
La información original estaba distribuida en dos archivos: movies_dataset.csv, que contiene datos generales sobre las películas, y credits.csv, enfocado en el elenco y equipo de producción.
Los datos no estaban normalizados, lo que requería una serie de transformaciones antes de que pudieran ser utilizados. 
Ademas, a estos archivos se le aplicaron una serie de funciones que desanidaban y normalizaban los datos, de tal manera, que los datos se pudieran normalizar.
Teniendo los datos normalizados, se procedio a seleccionar las columnas de datos que se hiban a necesitar para el desarrollo del sistema de recomendacion, como por ejemplo: 'Año, Director, Titulo de la pelicula,etc'.
Mientras que a las demas columnas se procedio a eliminar dado su irrelevancia para el desarrollo. 

Cuando se obtuvo las columnas elegidas para el desarrollo, se procedio a darles un tratamiento minucioso a estas. Se les quito valores nulos, valores faltantes, valores duplicados , caracteres inecesarios, se les aplico el tipo de dato correspondiente
Se renombraron columnas, se crearon columnas y las columnas de la cual se extrajo algun tipo de información fueron eliminadas, dado que su estadia en el archivo, añadia complejidad y confusión en el archivo. Finalmente y despeus de su respectivo tratamiento
la información se almaceno en un archivo .parquet. Este tipo de formato es ideal, por su eficiencia en la compresión y almacenamiento en columnas, lo que permite una lectura rápida y una menor utilización de memoria.

# Analísis Exploratorio de Datos (EDA)
En el notebook que tiene como nombre EDA, se puede observar un analísis detallado de los 2 archivos, que nos permite tener una mayor comprención de los datos. En este proceso, aparecieron bastantes  insights que nos permitieron entender otra cara
de los datos entregados, pudimos entender las tendencias en tematicas, años donde se lanzaron mas peliculas , genero favorito en toda la historia del cine, por poner por ejemplos. 
Los resultados del análisis, que incluyen la incidencia del presupuesto en las ganancias y la relación entre películas con altas votaciones y mayores ingresos, proporcionan información valiosa para el desarrollo del sistema de recomendación y la mejora del 
proceso de visualización. Todo esto permite sacar concluciones que pueden llevar a la toma de decisiones, dada la representación de los datos de manera vizual mediante graficas enfocadas a transmitir de la mejor manera los hallazgos encontrados
en este EDA(Analísis Exploratorio de datos).

# Modelo de recomendación
En el notebook Sistema de recomendación,  se presenta un análisis detallado del proceso de preparación de datos para el modelo de recomendación. Se optó por utilizar TfidfVectorizer para la vectorización del texto debido a la inconsistencia en los datos numéricos,
junto con la similitud del coseno para calcular la similitud entre películas.


# Creación de funciones
En el archivo **main.py** se detallan las funciones desarrolladas para la API, construida utilizando la librería FastAPI. Esta API permite acceder a las siguientes consultas sobre la base de datos procesada:

- **Películas por mes**: Permite seleccionar un mes del año y cuenta el número de estrenos ocurridos en ese mes.
- **Películas por día**: Permite seleccionar un día de la semana y cuenta el número de estrenos en ese día.
- **Score de película**: Proporciona el año de estreno y un valor numérico que representa la popularidad de una película, dado su título.
- **Votación de película**: Devuelve el año de estreno y, si la película cumple con un mínimo de valoraciones, el promedio de estas valoraciones, dado el título de la película.
- **Información de actor**: Ofrece el número total de películas en las que ha participado un actor, así como el porcentaje de retorno de sus películas a lo largo de su carrera, dado su nombre.
- **Información de director**: Muestra el número y la lista de películas dirigidas por un director, junto con el porcentaje de retorno de cada una, dado el nombre del director.

La API ha sido desarrollada utilizando FastAPI y todas las funciones han sido implementadas en el archivo **main.py**. Se ha comprobado que las funciones operan correctamente en un entorno local y están disponibles para su verificación en la plataforma Render.


[Aquí]() se puede encontrar la API desplegada.


