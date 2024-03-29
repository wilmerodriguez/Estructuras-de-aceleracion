# Estructuras de aceleración

### Performance inicial

La imagen inicial del tutorial 8, sin modificaciones, solo tiene una caja en la escena y entrega la siguiente gráfica de performance:

![imagen_inicial](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/inicial.PNG)
![](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/original.PNG)

Como se puede observar, hay un consumo de memoria de 433.

### Creación de más objetos

Para agregar más objetos a la escena, modifiqué la cantidad de cajas que se podían crear en la escena. Esto se puede ver en el código [modificacion.cpp](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/modificacion.cpp). Especfíficamente, en la línea de código #276 hasta la #467 se programan los parámetros de 23 cajas adicionales. Adicionalmente,en la línea de código #616 se crea una variable `factor` que se usa para crear una cantidad determinada de cajas con el material seleccionado y los parámetros de la primitiva `box` en las líneas de código #617 - 621. En este caso se crean 1000 cajas adicionales(`int factor = 1000;`). En las líneas de código #622 -644, se crean las 23 cajas adicionales con los parámetros establecidos previamente para cada caja. Finalmente, se crea el grupo de geometría de todas estas cajas creadas en las líneas de código #654 - 659. 

### Performance con aceleración

Para que la escena se carge con la estructura de aceleración, se deja activa la línea de código #692 `geometrygroup->setAcceleration( context->createAcceleration("Trbvh") )`. Esto da los siguientes resultados de performance: 

![](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/performance_con_aceleracion.PNG)
![](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/con_aceleracion.PNG)

Como se puede observar, la cantidad de FPS para generar más de 1000 cajas con estructura de aceleración es de 47.33, lo cual indica que apesar de la cantidad de objetos cargados, se obtiene una velocidad aceptable de FPS para la escena. También, se puede observar que la cantidad de consumo de memoria es de 438, la cual es mayor que la original y era lo que se esperaba pues se están creando más de mil objetos.

### Performance sin aceleración

Ahora, para cargar los objetos sin la estructura de aceleracion, se deja activa la línea de código #693 `geometrygroup->setAcceleration( context->createAcceleration("NoAccel") );`. Esto da los siguientes resultados de performance:

![](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/performance_sin_aceleracion.PNG)
![](https://github.com/wilmerodriguez/Estructuras-de-aceleracion/blob/master/sin_aceleracion.PNG)

Como se puede observar, la cantidad de FPS para generar más de 1000 cajas sin estructura de aceleración es de 1.00, lo cual indica que sin la estructura de aceleracióm la escena es muy lenta. También, se puede observar que la cantidad de consumo de memoria es de 439, la cual, al igual que la anterior, es mayor que la original por la cantidad de objetos creados.
