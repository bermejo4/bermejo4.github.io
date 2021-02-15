---
layout: post
title: Ping Analisis Script
---
*****
Este es un script que mediante el comando ping, el manejo de archivos y el computo de los datos que estos contienen, haya el número de paquetes enviados, el número de paquetes perdidos, el número de paquetes exitosos, la latencia de la red y el Jitter al intoducirle una dirección ip o una url.
Al ejecutar el script nos pedirá una dirección, esta dirección será a la cual vamos a hacer ping. Una vez que especifiquemos la dirección y pulsemos enter el programa empezará a correr y se imprimirá un mensaje por pantalla especificando como terminar con el programa y obtener los resultados; este mensaje dice "Teclee ctrl + c cuando desee terminar...", es decir, la combinación de teclas normal que se teclea en la terminal para la finalización de un proceso.
Cuando el programa haya terminado se imprimirá por pantalla los siguientes resultados:

- Número de paquetes enviados.
- Número de paquetes perdidos.
- Número de paquetes exitosos.
- Latencia.
- Jitter.

A la vez se crearán tres archivos ".txt" en el lugar en donde ha sido ejecutado el script. Estos tres archivos han sido usados para dar los anteriores resultados. Los archivos generados también pueden ser bastante útiles y son:

- "tmp.txt" : archivo donde se encuentra la salida o output de ejecutar el comando ping con la dirección specificada. Dependiendo del tiempo transcurrido desde el inicio del programa habrá mayor o menor cantidad de datos en este archivo.
- "time.txt": contine todos los tiempos en una sola columna vertical con el siguiente formato "time=" y el tiempo recogido de cada paquete enviado.
- "timesFiltered.txt": quizá este sea el archivo más importante, ya que contiene una columna única con los tiempos, en formato número y con ningún caracter más (es decir, no contiene la palabra "time=", solo contiene el numero). Con los datos de este archivo podemos sacar los resultados de la latencia y el jitter mediante un Excel, unicamente tenemos que copiar los datos de este archivo, pegarlos en Excel y calcular mediante la formula de la latencia y el jitter ambos resultados.

Observaciones: 
* Este script SOLO corre en Linux y no en la terminal de Mac.
* Si no se tuviera instalado, hay que instalar el paquete "bc" porque bash no maneja numeros decimales a la hora de hacer operaciones matemáticas.
* Si el programa ha estado ejecutandose durante mucho tiempo (por ejemplo media hora) el jitter tardará unos segundos en calcularse y mostrarse por pantalla.

Este es el script:

```shell
#!/bin/bash

echo "Especfica la dirección:"
read direccion
echo "Teclee ctrl + c cuando desee terminar..."
ping $direccion > tmp.txt

lost=$(grep -wo timeout tmp.txt | wc -w)
success=$(grep -wo from tmp.txt | wc -w)
cut -f 7 -d" " tmp.txt > times.txt  
cut -f 2 -d"=" times.txt > timesFiltered.txt
sed -i "1d" timesFiltered.txt
sed -i "$ d" timesFiltered.txt
sed -i "$ d" timesFiltered.txt

suma=$(grep . timesFiltered.txt | paste -sd+ | bc)
sum=$(($lost+$success))

echo "El programa ha terminado"
echo "Numero de paquetes enviados:"
echo $sum
echo "Numero de paquetes perdidos:"
echo $lost
echo "Numero de paquetes exitosos:"
echo $success
echo "La latencia es de:"
echo "scale = 2; $suma / $sum" | bc
pri=$(head -1 timesFiltered.txt)
total=0
i=0  
cmp=0
var2=0
for line in $(cat timesFiltered.txt)
do
        var1=$(echo "$line")
        resta=$(echo "scale = 2; $var2 - $var1" | bc)
        resta=${resta#-}
        cmp=$(echo "${resta%.*}")
        var2=$(echo $var1)
        total=$(echo "scale = 2; $total + $resta" | bc)
done
total=$(echo "scale = 2; $total - $pri" | bc)
sum=$(($sum-1))
echo "El jitter es de:"
echo "scale = 2; $total / $sum" | bc

```

* Resultado tras hacer ping de 8.8.8.8:
<div class="img-contenedor">
<img src="/images/projectsImages/redes/Ping Analysis/OutputPing8888Script.png" alt="8888" title="8888" width="25%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    width: 50%;
">
</div>
<br>
* Resultado tras hacer ping de 192.168.1.1 (Gateway):
<div class="img-contenedor">
<img src="/images/projectsImages/redes/Ping Analysis/OutputPing19216811Script.png" alt="19216811" title="19216811" width="25%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    width: 50%;
">
</div>