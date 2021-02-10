---
layout: post
title: Simulador para balances de trading 
---
*****

Este programa hecho en Html, Css y JavaScript sirve para calcular los rendimientos finales de una inversión en criptomoneda durante un día, una semana o el tiempo marcado.
Este programa se divide en 4 subprogramas de diferentes características:

* ### Simulación Diaria:
Esta simulación consite en dividir la cantidad de dinero que se va a usar en la inversión inicial en 6 partes iguales, y con cada una de las partes invertirlas en una criptomoneda diferente. Pasadas 24 horas anotar el rendimiento sacado de cada inversión hecha (el tanto por ciento que aparece en el mercado que hayamos invertido), y además anotar como último paso la comisión que se nos aplica por dicho trading. El programa nos dará un resultado final del tanto por ciento que en ese día hayamos ganado o perdido.

Interfaz de la simulación diaria:
<div class="img-contenedor">
<img src="/images/codeImages/Html/SimulacionDiaria.png" alt="MenuImage" title="MenuImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>

* ### Simulación Flexible:
La simulación flexible es algo más compleja, está destinada a dividir la cantidad de dinero que queramos invertir en un número concreto de partes con las que nostros queramos trabajar, es decir, si en la anterior simulación diaria dividíamos la inversión en 6, ahora ese número lo podemos adaptar dependiendo de nuestra estrategia de trading. Una vez que introduzacamos este número debemos indicar también la comisión que se nos aplicará por dicho trading y le damos a "Siguiente", después de esto se nos desplegarán un número de campos en blanco en los que introduciremos nuestros datos de porcentajes de lo registrado en las últimas horas dependiendo del número que hayamos concretado al principio del programa. Una vez hayamos escrito nuestros porcentajes el programa nos calcula un computo final del porcentaje de dinero que hemos ganado o perdido ese día. Por último en la barra inferior podemos hacer un cálculo del dinero del que disponemos tras ese día de trading dependiendo de lo ganado o perdido; además podemos ponerlo en dolares, en euros o en BNB si es tu moneda de referencia.

Interfaz de la simulación flexible con un ejemplo:
<div class="img-contenedor">
<img src="/images/codeImages/Html/SimulacionFlexible.png" alt="ProsImage" title="prosImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>


* ### Simulación Semanal:
La simulación semanal es bastante parecida a la simulación diaria, lo único que cambia es que se deberá anotar los porcentajes obtenidos durante la semana en la simulación diaria y luego finalmente introducirlos en este programa. Además en comparativa con la simulación diaria este programa tiene una barra lateral en donde se indican los valores máximos y mínimos de la semana obtenidos.

Interfaz de la simulación semanal:
<div class="img-contenedor">
<img src="/images/codeImages/Html/SimulacionSemanal.png" alt="HospImage" title="HospImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
">
</div>

* ### Calcular Porcentajes:
Esta parte del programa está destinada a obtener el porcentaje concreto si a lo mejor se nos ha pasado anotar los porcentajes o si deseamos calcular un porcentaje en concreto.
Como primer paso debemos indicar el número de porcentajes que deseamos calcular, después daremos en "Siguiente", y se desplegarán el número de campos que hayamos indicado. En el primer campo en blanco, aquel que está después de la palabra campo, indicaremos el nombre de la criptomoneda, y posteriormente su valor inicial, y en el campo de su derecha indicaremos su valor final; al terminar de rellenar todos los campos en blanco daremos al botón "Calcular", esto nos imprimirá por pantalla el porcentaje de cada criptomoneda y además el porcentaje combinado de las criptomonedas.
Finalmente en la barra inferior podemos introducir la cantidad de dinero que hayamos invertido para ver cual es nuestro saldo final trás esta operación. Al igual que anteriormente podemos concretar esta cantidad en euros, dolares o Binance coin si es nuestra moneda de referencia.

Interfaz del cálculo de porcentajes:
<div class="img-contenedor">
<img src="/images/codeImages/Html/CalcularPorcentajes.png" alt="MenuImage" title="MenuImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>


### Menú principal:
En este menu podemos encontrar los 4 botones que nos llevan a los 4 subprogramas diferentes de esta simulación.

Interfaz del menú principal:
<div class="img-contenedor">
<img src="/images/codeImages/Html/Inicio.png" alt="MenuImage" title="MenuImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>



*****

  <a href="https://github.com/bermejo4/SimuladorCripto" target="_blank"> Link para el código en GitHub</a>

*****


