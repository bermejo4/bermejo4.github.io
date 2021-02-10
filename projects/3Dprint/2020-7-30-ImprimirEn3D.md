---
layout: post
title: Imprimir en 3D desde cero
---
*****
### Cosas necesarias:
- Un ordenador
- Una impresora 3D
- Manual de instrucciones y configuraciones de tu impresora 3D (físico o de internet).

### Software necesario:
En primer lugar, necesitamos un software de Diseño gráfico 3D, hay muchos en el mercado hoy en día, como pueden ser Autocad, Sketch-up, Rhinoceros… Dependiendo de la complejidad de nuestros diseños y la potencialidad que le queramos sacar utilizaremos un software u otro (también hay que tener en cuenta la calidad de nuestra impresora 3D, ya que si esta no ofrece un acabado muy detallista la precisión del software de diseño utilizado no servirá de mucho). 
En nuestro lugar, y como estamos empezando utilizaremos Sketch-up, ya que ofrece un software limpio, versátil y fácil de usar, con una alta precisión, aunque no con tanta profesionalidad que los otros mencionados… pero para empezar estará bien. 

Hay versiones gratuitas de sketch-up temporales (de un mes cómo máximo), podemos usar una de ellas para empezar a diseñar. 

Este software se instala muy fácilmente. 

Hay un software, o mejor dicho extensión, del propio Sketch-Up que es necesario instalar por motivos que después explicaremos. 

Con Sketch-up tenemos disponible un centro de extensiones en el que descargarnos software extra para completar nuestros proyectos o trabajos. Nosotros nos descargaremos una extensión que convierte nuestro diseño guardado como “.skp”, en un diseño con el formato “.stl”. Con poner en la barra del buscador de extensiones la palabra “stl” nos aparece directamente la extensión que deseamos. Una vez que tengamos la extensión le damos a “descargar” (o “instalar” en algunos casos). Para este paso hay que tener una cuenta en Sketch-Up, pero si te lo has descargado de la página oficial posiblemente ya la tengas e incluso esté sincronizada con tu Sketch-Up.

Centro de extensiones de Sketch-Up:
<img src="/images/projectsImages/3Dprint/Imprimir3D_CentroDeExtensiones.png" alt="CentroDeExtensionesSKP"
	title="ExtensionesSKP" width="100%"/>

Extensión Stl que debemos instalar:
<img src="/images/projectsImages/3Dprint/ExtensionStl.png" alt="ExtensionStl"
	title="ExtensionesStl" width="100%"/>

De cara a nuestra impresora 3D necesitamos 2 softwares especialmente, uno de ellos es la interfaz gráfica que nos permite comunicarnos con nuestra impresora 3D (Repetier-Host), y el otro es un laminador o trasformador a g-code (Slic3r o Cura). 

Cada fabricante de impresoras 3D recomiendan un software de interfaz gráfica diferente, pero todos ellos deben desempeñar la misma acción, que es la de permitir interactuar al usuario con su impresora 3D. Recomiendo descargar la última versión de “Repetier-Host” y de “Slic3r” para el sistema operativo que desee, posteriormente ya los configuraremos.

### Diseño 3D:
Si ya tenemos instalado nuestro software de diseño preferido recomiendo interactuar con las herramientas de este.
Una vez que lo tengamos instalado, hayamos interactuado con sus herramientas y sepamos más o menos lo que hace cada una podemos empezar a diseñar todo aquello que tengamos en la cabeza (es importante que para cualquier diseño que vayamos a pasar luego a la impresora 3D las medidas estén en milímetros, por lo tanto hay que tener en cuenta que muchos programas de diseño en 3D al principio nos solicitan elegir la plantilla que vayamos a usar, y debemos seleccionar la de milímetros). Personalmente recomiendo empezar por algo sencillo, como un cubo o una pirámide, y posteriormente ir subiendo de nivel.

Una vez que tengamos aquello que nos hemos propuesto diseñar lo guardamos en nuestro ordenador. 
Ahora viene una parte muy importante y es guardarlo en un formato que posteriormente nuestra impresora pueda manejar. Hay varios formatos disponibles, pero el más famoso y usado es el “.stl”. 

Como anteriormente nos hemos descargado la extensión este paso es muy sencillo.
Una vez tengamos todo listo (extensión instalada y diseño abierto) nos iremos a la barra de herramientas superior, a “archivo” (o “file”) y pulsaremos en “exportar como stl” (o “export as stl”), nos saldrá una ventana preguntándonos las medidas y el formato del archivo, nos tenemos que asegurar que las medidas estén en milímetros y el formato del archivo en “ASCII”; y finalmente le daremos a “exportar” (o “export”).

Esta sería la configuración: 

<img src="/images/projectsImages/3Dprint/Export.png" alt="ExportImage" title="ExportImage" width="75%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: inherit;
">

Si únicamente queremos probar nuestra impresora 3D, y por algún motivo no disponemos del tiempo necesario para crear un diseño, podemos recurrir a alguna de las grandes galerías de diseños stl de internet. Una de las más famosas y usadas es: <a href="https://www.thingiverse.com/" target="_blank">www.thingiverse.com</a>
, en ella podrás encontrar numerosos diseños hechos por otros entusiastas de la impresión 3D, descargarlos (se descargará un archivo comprimido que en su interior tendrá archivos en formato stl) e imprimirlos con facilidad.
 
### Impresión 3D:

Lo primero de todo, recomiendo leer bien el manual de la impresora y configuraciones.

Para imprimir en impresión 3D, primero ajusta la impresora con las configuraciones recomendadas por las instrucciones de la impresora, (sino las encuentras siempre puedes recurrir a internet donde encontrarás el manual de la marca o recomendaciones de personas que ya conocen su impresora 3D), posteriormente ajusta las configuraciones del filamento (temperatura del extrusor, de la cama, cantidad de extrusión) siguiendo las instrucciones del fabricante (aunque muchas veces estas no sean las verdaderamente idóneas para tu impresora y tengas que buscar tu la configuración perfecta de esta mediante lógica; y prueba y error como última salida). Para toda esta configuración cada marca de impresora recomienda un software diferente; por ser intuitivo y gratuito yo siempre recomiendo “Repetier-Host”.
Una vez que tengamos todo configurado se necesita un programa que trasforme nuestro diseño en un formato de láminas que nuestra impresora sepa leer para saber en que coordenadas exactas debe poner plástico y en cual no, este formato se llama “G-Code”. 

Muchos de los softwares de interfaz gráfica para la impresión, como el anteriormente citado Repetier-Host viene con un laminador o software de laminación incluido bastante bueno para la tarea de la transformación de la figura stl a g-code. 

Alguno de los softwares de laminación más conocidos son Slic3r y Cura. Personalmente prefiero Slic3r porque tiene más opciones de configuración, pero Cura para empezar también está bien.

Una vez que tengamos instalado nuestro laminador preferido, lo configuramos con la interfaz gráfica de la impresora, en nuestro caso Repetier-Host. En algunos casos este paso de configuración da problemas porque Repetier-Host no encuentra el directorio en el que está Slic3r o Cura, para ello averiguamos la ruta en donde se encuentra en nuestro ordenador y la copiamos; posteriormente iremos a los ajustes de Repetier-Host y le indicaremos la ruta en donde está nuestro laminador determinado en "Preferencias" > "Slic3r" > "Buscar". 

Al dar en "Preferencias" debería salir una ventana como esta y seleccionar "Buscar" o "Browser" e introducir la ruta de la aplicación: 
<img src="/images/projectsImages/3Dprint/DirectorioSlic3r.png" alt="DirectorioSlic3r" title="DirectorioSlic3r" width="75%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: inherit;
">


Una vez que tengamos todo listo cargaremos nuestro archivo stl en Repetier-Host y daremos al botón de slice con Slic3r (o cura, o nuestro laminador favorito), si no ocurre nada posiblemente tengas el problema planteado anteriormente (Repetier-Host no encuentra el directorio del laminador).

Si todo ha salido correctamente se te mostrará una visualización de tu diseño Stl cargado, pero si te fijas y haces zoom podrás ver que el diseño está formado por líneas o hilos, esto es normal y es señal de que lo estamos haciendo correctamente. Lo que se ve es el camino que seguirá el extrusor y por donde soltará plástico para dar lugar a nuestra figura. 

<img src="/images/projectsImages/3Dprint/Laminacion.png" alt="Laminacion" title="Laminacion" width="75%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: inherit;
">

Otra de las cosas que también nos aparecerá posiblemente es el G-code, un código formado por números y coordenadas (en algunos casos este código se puede cambiar, pero únicamente si se entiende lo que se está cambiando y el porqué de esa acción).

Ejemplo de G-Code:
<img src="/images/projectsImages/3Dprint/EjemploDeGCode.png" alt="EjemploDeGCode" title="EjemploDeGCode" width="75%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: inherit;
">

Una vez que tengamos nuestra impresora encendida, conectada con la interfaz gráfica (Repetier-Host), configurada y configurado el Slic3r, y hayamos obtenido el G-code, podemos dar al botón “imprimir” (o “Run” en algunas interfaces) y nuestra impresora empezará su acción. 

Es aconsejable que se pulse en la interfaz gráfica los botones de calentar cama y calentar extrusor mucho antes de darle a imprimir para ahorrarnos tiempo, porque dependiendo del tipo de impresora esta acción puede llevar de 2 a 10 minutos hasta alcanzar las temperaturas optimas.

Como he dicho al principio recomiendo leer bien el manual de la impresora y configuraciones, antes de nada.