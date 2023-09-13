Implementacion datadog portal

Creacion Cuenta DataDog

Primer paso es ir a <https://www.datadoghq.com/> y crear una cuenta

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.001.png)

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.002.png)

Llenaremos los datos, el telefono no es necesario.

**La primera opcion es importante mantenerla en US5.**

Ahora ocuparas selecionar lo siguiente, no tiene importancia.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.003.png)

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.004.png)

Se pueden quedar vacios los campos.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.005.png)

Nos daran esta pagina, ocupamos selecionar windows.

Primero ocupams copiar el api key dandole click en el icono de copiar que sale en la foto de arriba

Instalacion Agente DataDog

Ocupamos descargar el instalador del link dado anteriormente

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.006.png)

Dejara un archivo![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.007.png) Ahora se ocupara instalar ese archivo

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.008.png)

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.009.png)

Aqui agregaremos la key copiada anteriormente.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.010.png)

Aqui elegiremos la opcion de us5

Pedira agregar un usuario y contraseña y daremos a continuar Ya con eso estara instalado el angente el equipo

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.011.png)

Ahora se abrira la siguiente pagina

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.012.png)

Indicando que el agente esta conectado.

Es todo lo que se hara por este lado con el agente

Ya podemos ir a <https://us5.datadoghq.com/> a ver nuestro agente

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.013.png)

Debera salir un rombo ese es nuestro equipo. Este proceso puede tardar como 5 min en aparecer al actualizar la pagina.

Nota: si no aparece reiniciar el agente, este se puede reiniciar desde la barra de tareas

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.014.png)

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.015.png)

Tarda como 30s a 1min

Ya con esto pasaremos a el proyecto en java

PROYECTO JAVA

Ocupamos descargar la siguiente libreria del versionador. En la carpeta LibreriasABB

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.016.png)

Ahora ocupamos ir a la siguiente ruta en el disco C:\payara41\glassfish\domains\domain1\config Para entrar a este archivo

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.017.png)

Buscaremos con ctrl + f jvm-options Aproximadamente en la linea 225

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.018.png)

Aqui agregaremos las siguiente lineas

<jvm-options>-javaagent:C:/Proyectos/LibreriasABB/dd-java-agent.jar</jvm-options> <jvm-options>-Ddd.logs.injection=true</jvm-options> <jvm-options>-Ddd.env=DEV</jvm-options> <jvm-options>-Ddd.service=DEV-Aduasis</jvm-options>

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.019.png)

La primera linea es importante cambien la ruta en la cual tengan la libreria dd-java-agent descargada anteriormente, en mi caso la tengo en la carpeta libreriasABB pero ustedes la tendran donde la descargaron, probablemente en libreriasABB , si no, solo seria cambiar esa carpeta

nota: no colocar ruta con espacio por ejemplo c:/proyecto netbeans/ ya que causa error de lectura

Ya que tengamos guardamos el archivo y podremos cerrar esa carpeta.

Ahora pasaremos a las variables de entorno

En el buscador de windows buscaremos variables de entorno

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.020.png)

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.021.png)

En este apartado agregaremos las variables de entorno

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.022.png)La primera es con el api key que se te genero al crear tu cuenta de datadog esta es la mia por ejemplo.

DD\_API\_KEY 3fb89a6c93356310a9cd6fe80559e6e

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.023.png)

La segunda es la region que estableciste al crear la cuenta, esta es la que recomende al incio. DD\_APPLICATION\_ID

us5.datadoghq.com

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.024.png)

Ya con estas variables podemos guardar todo y salir de ahi. Quedara de la siguiente manera

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.025.png)Ya que tenemos todas estas configuraciones podremos ir a el proyecto de payara y correrlo. Como normalmente se hace.

Por ejemplo un deploy o un debug.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.026.png)

Esperamos unos segundos y probamos.

Ya deberia estar detectando datadog la informacion, iremos a [https://us5.datadoghq.com/help/quick_start ](https://us5.datadoghq.com/help/quick_start)Y veremos nuestro equipo

}![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.027.png)

Si no aparece nada reiniciamos el agente de nuevo y recargamos la pagina.

Puede tomar unos 5min

Deberia decir al menos 1 host en su caso, daran en expanded host map

Y deberia salir el siguiente rombo con estos 2 iconos, si es asi es un exito la configuracion.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.028.png)

Para ver la informacion iremos al menu lateral izquierdo de datadog

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.029.png)

Presionaremos en APM

Deberia mostrarte la siguiente ventana

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.030.png)

El que nos interesa usar es dev-aduasis presionaremos en el.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.031.png)

Aqui empezaremos a ver informacion al movernos a traves del proyecto portal

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.032.png)

Esas pestañas como service sumery pueden minimizarlas para tener una vista asi

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.033.png)

Aqui se veran las peticiones hechas desde portal local. Por ejemplo podemos ir a este get

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.034.png)

Al darle click se abrira esta ventana

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.035.png)

Donde podremos ir a ver cosas como la siguiente

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.036.png)

Al darle click

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.037.png)

Si seleccionamos la pestaña SQL Queries veremos todos los que hace.

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.038.png)

Tambien podemos ver otra tipo de informacion al selecionar una solicitud

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.039.png)

En el dependecy map

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.040.png)

Si lo selecionamos podremos ver lo siguiente

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.041.png)

Recordar siempre tener activa el monitoreo

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.042.png)

Esta en la parte superior de la pagina

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.043.png)

Aqui podremos ajustar el tiempo desde donde queremos tener registros y tiene que estar encendido quedando ese icono.

Si esta el icono de play entonces no esta recopilando la informacion

Nota: es el rango de tiempo para ver la informacion, siempre y cuando estuviera encendido el servicio.

El agente se ve asi en el menu de iconos![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.044.png)pero se puede revisar que este encendido dirigiendonos a

<http://127.0.0.1:5002/>

Dira conected agento o disconected agent

Para encenderlo o apagarlo es en click derecho

![](Aspose.Words.dcf0b232-0249-4dff-8673-c7de16754237.045.png)
