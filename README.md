# TP4
Clasificación de imágenes en GEE y matriz de confusión
- Universidad de Costa Rica 
- GF-0618 FOTOGRAMETRÍA Y TELEDETECCIÓN
- MSc.María José Molina Montero
- Estudiantes: Steven Guillén-Ana López  
# Objetivo 
1.	Desarrolle un código para clasificar una imagen Landsat 8 TOA, de un área en Guanacaste

## Procedimiento
- Genere curvas de reflectancia para cada una de las coberturas definidas e interprételas brevemente

- Para el proceso de clasificación, utilice los clasificadores: Classification and Regression Trees (CART)–ee.Classifier.smileCart y luego realice otra clasificación pero con RandomForest–ee.Classifier.smileRandomForest 
- Compare los resultados de ambos clasificadores 
- Realice la matriz de confusión para ambos clasificadores
- Realice un mapa con su respectiva leyenda
- Conclusiones del ejercicio, aplicaciones de las clasificaciones de imágenes satelitales. Lecciones aprendidas
## Conceptos teóricos 
- Realice una introducción donde explique ¿qué son las clasificaciones supervisadas? ¿Qué es el Machine Learning y cómo se conecta con la teledetección?

La clasificación supervisada es fundamental pues gracias a ello se puede identificar un determinado píxel y clasificarlo para crear distintas categorías.En este tipo de clasificación la persona experta tiene el control del proceso y asigna áreas de entrenamiento conocidas para que posteriormente el algoritmo realice la identificación donde encuentre gupos de píxeles similares a los puntos o polígonos distribuidos previamente en en área de estudio.Finalmente es necesaria una validación del procedimiento.

Para el análisis de imágenes satelitales la clasificación de coberturas terrestres consiste en la agrupación de clases espectrales con determinadas respuestas que finalmente proporciona clases informativas fundamentales para identificar la evolución de un área y los cambios que surgen producto de las dinámicas en la zona de estudio.


La clasificación de imágenes satelitales más utilizada es la basada en píxeles 
> *la clasificación supervisada de imágenes, que es el que se lleva a cabo para encontrar propiedades comunes entre un conjunto de datos y clasificarlos dentro de diferentes rangos, de acuerdo a un modelo de clasificación* (García et al.1998 citado en Rojas y Medina, 2021,p.92).

