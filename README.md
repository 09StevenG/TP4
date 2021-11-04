# TP4
Clasificación de imágenes en GEE y matriz de confusión
- Universidad de Costa Rica 
- GF-0618 FOTOGRAMETRÍA Y TELEDETECCIÓN
- MSc.María José Molina Montero
- Estudiantes: Steven Guillén-Ana López  
# Objetivo 
1.	Desarrolle un código para clasificar una imagen Landsat 8 TOA, de un área en Guanacaste

[Código resultante en GEE](https://code.earthengine.google.com/af62011dca308889c00cfd8cb9c129d6)

## Conceptos teóricos 
- Realice una introducción donde explique ¿qué son las clasificaciones supervisadas? ¿Qué es el Machine Learning y cómo se conecta con la teledetección?

La clasificación supervisada es fundamental pues gracias a ello se puede identificar un determinado píxel y clasificarlo para crear distintas categorías.En este tipo de clasificación la persona experta tiene el control del proceso y asigna áreas de entrenamiento conocidas para que posteriormente el algoritmo realice la identificación donde encuentre gupos de píxeles similares a los puntos o polígonos distribuidos previamente en en área de estudio.Finalmente es necesaria una validación del procedimiento.

Para el análisis de imágenes satelitales la clasificación de coberturas terrestres consiste en la agrupación de clases espectrales con determinadas respuestas que finalmente proporciona clases informativas fundamentales para identificar la evolución de un área y los cambios que surgen producto de las dinámicas en la zona de estudio.La clasificación de imágenes satelitales más utilizada es la basada en píxeles 

> *la clasificación supervisada de imágenes, que es el que se lleva a cabo para encontrar propiedades comunes entre un conjunto de datos y clasificarlos dentro de diferentes rangos, de acuerdo a un modelo de clasificación* (García et al.1998 citado en Rojas y Medina, 2021,p.92).

El aprendizaje automático consiste en un subconjunto de la inteligencia artificial en el que los datos estructurados se procesan con un algoritmo para resolver un problema. Su relación con la Teledetección surge en el momento de realizar procesamientos geoespaciales aportando soluciones automatizadas que permiten realizar procesamientos con mayor facilidad y exactitud.

En el presente trabajo práctico se visualiza como las indicaciones realizadas (con puntos de entrenamiento) para la identificación de coberturas, interactúan con un algoritmo a lo largo del área seleccionada en la región de Guanacaste.  

> *Se han empezado a unir herramientas de sistemas de información geográfica con inteligencia artificial para volver cada vez más eficientes los análisis. Una de las ramas de la inteligencia artificial que más se ha aplicado en el uso de los SIG es el aprendizaje automático (Machine Learning en inglés). Tal y como lo explica Lauren Bennett, líder del desarrollo de software para Análisis Espacial y la Ciencia de Datos en Esri, el aprendizaje automático es un “conjunto de técnicas y algoritmos basados ​​en datos que automatizan la predicción, clasificación y agrupación de datos”. En términos generales, son algoritmos alimentados con información para aprender de ésta y poder replicarse en otras situaciones* [esri Pánama, 2021](https://www.esri.pa/arcgisblog/los-resultados-de-la-fusion-entre-los-sig-y-el-aprendizaje-automatico/). 

## Procedimiento
- Genere curvas de reflectancia para cada una de las coberturas definidas e interprételas brevemente
![](grafico1.png) ![](grafico2.png)

> Se realiza una clasificación de los píxeles en función de la información espectral. Las firmas espectrales nos permiten conocer la reflectancia de una determinada cobertura en distintas longitudes de onda. 
Hay un comportamiento similar al visualizar las firmas espectrales resultantes. El suelo desnudo presenta alta reflectancia en el espectro visible (azul, verde, rojo) y va disminuyendo hasta en el infrarrojo lejano.  El bosque y los cultivos tienen una alta reflectancia en el segmento rojo e infrarrojo cercano debido a la clorofila presente en estas coberturas. El Urbano presenta alta reflectancia en el espectro rojo pero se mantiene constante hasta el infrarrojo lejano.
Claramente surgen algunas diferencias muy marcadas como en el caso de las nubes que presentan una alta reflectancia en todo el espectro en comparación con las demás coberturas utilizadas. En contraste con los cuerpos de agua que solamente presentan alta reflectancia en el espectro de onda azul.


- Para el proceso de clasificación, utilice los clasificadores:
 ### Classification and Regression Trees (CART)–ee.Classifier.smileCart
![](chart.png)

> Los árboles de clasificación y regresión (CART) es un método que utiliza datos históricos para construir árboles de clasificación o de regresión, los cuales son usados para clasificar o predecir nuevos datos. Estos árboles CART pueden manipular
fácilmente variables numéricas y categóricas.(Sepúlveda, 2012, p.176)

En este caso los datos "históricos" son los puntos que catalogamos en una determinada cobertura con el respaldo de la imagen de color verdadero, además de la imagen satelital con la que cuneta GEE.



### RandomForest–ee.Classifier.smileRandomForest 
![](ra.png) 

> *Random Forest es uno de los algoritmos de clasificación de imágenes más usados en teledetección. Una de  sus ventajas es que aporta una estimación interna de exactitud mediante una forma de validación cruzada. Sin embargo, esta estimación subestima el error de predicción al clasificar coberturas del suelo con áreas de  entrenamiento compuestas por varios píxeles, ya que se viola la necesaria independencia estadística entre  casos de entrenamiento y de validación.*(Cánovas et al.,2016,p.360)

### Clasificación en cuenca Tempisque sin la variable Nubes 
![](tempiscuenca.png) 

- Compare los resultados de ambos clasificadores 



- Realice la matriz de confusión para ambos clasificadores
 > ![](CART.png)  _CART_
 
 >  ![](RANDOM.png) _RANDOM FOREST_

Al comparar los resultados de cada clasificación respecto a la verdad del terreno, en ambas matrices la clasificación del bosque y los cuerpos de agua es óptima. Los errores surgen para la clasificación de cultivos, uso de suelo y urbano pues se presentan valores en una clase que pertenecen a otra. Con el método Random Forest los errores de omisión y comisión dismunuyen un poco pero se presenta la misma problemática.
    

- Conclusiones del ejercicio, aplicaciones de las clasificaciones de imágenes satelitales. Lecciones aprendidas

Cánovas-García, F., Alonso-Sarría, F., & Gomariz-Castillo, F. (2016). Modificación del algoritmo Random Forest para su empleo en clasificación de imágenes de Teledetección. In Aplicaciones de las Tecnologías de la Información Geográfica (TIG) para el desarrollo económico sostenible XVII Congreso Nacional de Tecnologías de Información Geográfica, Málaga (Vol. 29, No. 30, pp. 359-368).

Sepúlveda, J. F. D., & Morales, J. C. C. (2013). Comparación entre árboles de regresión CART y regresión lineal. Comunicaciones en Estadística, 6(2), 175-195.
