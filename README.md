![Iron Hack](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/ironhack.png)
# Análisis instántaneo de competencia

- El 75% de las pymes no llegan a los dos años
- Actualmente en México hay mas de 5 millones de pymes
- Se crean mas empresas de las que mueren 

Principales causas de muerte:

- Ingresos insuficientes (68%)
- Falta de Indicadores (48%)
- Falta de Análisis (44%)

### Intro 
Utilizando la base de datos abierta y complementandola de otras bases de datos, creamos un modelo el cual arroja información util para saber la *viabilidad de un proyecto* que aun se encuentre en idea y asi poder plantear estrategías para abordar el proyecto de una manera mas exitosa, asi como poder cuantificar el riesgo que esta tiene en el mercado actual.

### Data Utilizada
- Api de INEGI
- Bases de datos especiales de INEGI

### Alcance

El estudio abarca toda la Ciudad de México.
Se abarcan solo empresas Retail que cuenten con un establecimiento fisico y que se encuentren registrados en DENUE.
El modelo entregara un PDF.

### Modelo

El modelo tiene como entrada:
-Latitud y longitud de donde sera el establecimiento
-Giro del proyecto
-Rango de impacto en mts (Un oxxo no tendra el mismo rango de impacto que una tiendita de la esquina o un Walt-Mart)

Se hace una consulta atravez del API de INEGI
![Head de documento PDF](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/Imagen1.jpg)
y se ecnuentran el numero total de empresas que serían tanto competencia indirecta como directa.

despues en el análisis aparecen los principales giros (más especificado) de las empresas que se analizan, asi como, el tamaño de estas empresas
![Principales giros](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head2.jpg)
![Tamaño de empresas](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head3.jpg)

se hace merge con otra base de datos de los establecimientos de CDMX atravez de su id y se sabe el año de incorporación a DENUE
*Este paso es muy importante, ya que si tuvieramos el año de funcdación de las empresas podriamos generar un modelo el cual prediga cuantas empresas nacerian del mismo giro, en nuestro rango de impacto)
este esta tanto en año como en mes

![Año de integración](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head5.jpg)
![Mes de integración](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head4.jpg)

se crea una tabla en la cual se muestra la esperanza de vida en años y en probabilidad **la tabla se mantendra igual ya que el alcance del estudio es solo CDMX**

![Tabla esperanza de vida](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head6.jpg)

Finalmente se hace match pero ahora por clave de AGEB y Manzana para sacar la población, esta información es desactualizada (2010) ya que solo en este censo encontre información de población tan detallada como la que requeria, el resultado arrojado fue:

![Tabla esperanza de vida](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/images/head7.jpg)
La cual muestra la población total y económicamente activa que se encunetran en las diferentes manzanas de todos los establecimientos o competencia que hemos encontrado

En este [link](https://github.com/rogerzadi/ModeloSupervivencia/blob/master/simple_demo.pdf) se muestra un ejemplo del resultado del modelo.



