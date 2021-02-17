---
layout: post
title: Farmacia Digital
---
*****
Este es un proyecto para demostrar que a través de una aplicación python fácil de consola se puede representar la administración del stock o inventario de una farmacia. 
Es un programa base, sencillo, desarrollado todo el código en un bloque y cuyos datos se pueden exportar a un archivo tanto de extensión ".txt" como en extensión ".csv".  
Al final de la ejecución del programa, si se desea se pueden exportar los datos a un archivo de extensión ".csv" y abrir estos en un programa de celdas, es decir, en un programa del estilo 'Microsoft Excel'.  
Este programa no es muy complejo; su finalidad final es demostrar la versatilidad de este leguaje para poder crear programas robustos y versátiles en poco tiempo y con pocas líneas de código. 

## Código Python: 
```python
from io import open
from datetime import date
from datetime import datetime

def alta(catalogo):
    nombre,precio,codigo,caducidad,necesitaReceta=pedirProducto()
    productoAlta=producto(nombre,precio,codigo,caducidad,necesitaReceta)
    catalogo.append(productoAlta)


def baja(catalogo):
    codigo=pedirSoloCodigo()
    print('El codigo introducido es:'+str(codigo))
    a=0
    for p in catalogo:
        if p.codigo==codigo:
            a=a+1
            catalogo.remove(p)
    if a>0:
        print('Se han eliminado '+str(a)+' elementos del inventario.')

def consulta(catalogo):
    codigo=pedirSoloCodigo()
    for p in catalogo:
        if p.codigo==codigo:
            print('Si el producto está en el programa')
            print('Su precio es de:'+str(p.precio))

def modificacion(catalogo):
    codigo1=input('Introduce el codigo del fármaco que desea actualizar:')
    nombre=input('modifique el nombre.')
    codigo2=input('modifique el codigo.')
    precio=input('modifique el precio.')
    print('modifique la fecha de caducidad:')
    dia=int(input('Dia:'))
    mes=int(input('Mes:'))
    anho=int(input('Año:'))
    caducidad=datetime(anho, mes, dia)
    receta=input('Necesita Receta?(si/no)')
    if receta=='Si' or receta=='SI' or receta=='si':
        necesitaReceta=True
    else:
        necesitaReceta=False
    for p in catalogo:
        if p.codigo==codigo1:
            catalogo.remove(p)
    productoModificado=producto(nombre,precio,codigo2,caducidad,necesitaReceta)
    catalogo.append(productoModificado)

def listado(catalogo):
    print('--->Inventario de los medicamentos<---')
    for product in catalogo:
        product.mostrarDetalles()

def pedirProducto():
    nombre=input('Introduzca el nombre del medicamento:')
    codigo=input('Introduzca el código:')
    precio=input('Introduzca el precio:')
    print('Introduzca la fecha de caducidad:')
    dia=int(input('Dia:'))
    mes=int(input('Mes:'))
    anho=int(input('Año:'))
    caducidad=datetime(anho, mes, dia)
    receta=input('Necesita Receta?(si/no)')
    if receta=='Si' or receta=='SI' or receta=='si':
        necesitaReceta=True
    else:
        necesitaReceta=False
    return nombre,precio,codigo,caducidad,necesitaReceta

def pedirSoloCodigo():
    codigo=input('Introduzca el código del producto:')
    return codigo

def manejoFicheros(nombre, modo):
    file = open(nombre, modo)
    print('test')
    return file

def guardado(catalogo):
    f=manejoFicheros('Data.txt','w')
    f.write(str(catalogo))
    print('Guardado correctamente. En Data.txt')

def exportarComoCSV(catalogo):
    f=manejoFicheros('Data.csv','w')
    f.write('Nombre,Precio,Codigo,Caducidad,Prescripcion,\n')
    for farma in catalogo:
        f.write(farma.datosParaCSV())
        f.write('\n')

    print('Guardado correctamente. En Data.csv')
        


def recuperacion():
    lista=[]
    return lista
 
def imprimirMenu():
    print("\n\n--- Farmacia Digital ---")
    print('\n Seleccione la operacion que desea utilizar en la farmacia:')
    print("1.Alta de un fármaco.")
    print("2.Baja de un fármaco.")
    print("3.Consulta de un fármaco.")
    print("4.Modificación de un fármaco.")
    print("5.Listado de los medicamentos de la Farmacia. (Inventario)")
    print("6.Guardado")
    print('7.Exportar como CSV.')
    print("0. Back")
    return int(input("Select an option: "))



class producto():
    def __init__(self, nombre, precio, codigo, caducidad, prescripcion):
        self.nombre=nombre
        self.precio = precio
        self.codigo = codigo
        self.caducidad=caducidad
        self.conPrescripcion=prescripcion
    
    def mostrarDetalles(self):
        print('\n-El precio de:'+str(self.nombre)+' con codigo:'+str(self.codigo)+' es de:'+str(self.precio)+' €.')
        print('Su fecha de caducidad es:'+str(self.caducidad))
        if self.conPrescripcion==True:
            print('El '+str(self.nombre)+' necesita prescripción médica.')
        else:
            print('El '+str(self.nombre)+' NO necesita prescripción médica.')
        
    def CambiarPrescripcion(self):
        if self.conPrescripcion:
            self.conPrescripcion=False
        else:
            self.conPrescripcion=True
            
    def datosParaCSV(self):
        linea=str(self.nombre)+','+str(self.precio)+','+str(self.codigo)+','+str(self.caducidad)+','+str(self.conPrescripcion)
        return linea

option=imprimirMenu()
catalogo=[]


while option!=0:
    if option>7 or option<0:
        print('Error Opción no válida')
    else:
        if option == 1:
            alta(catalogo)
        elif option == 2:
            baja(catalogo)
        elif option == 3:
            consulta(catalogo)
        elif option == 4:
            modificacion(catalogo)
        elif option == 5:
            listado(catalogo)
        elif option==6:
            guardado(catalogo)
        elif option==7:
            exportarComoCSV(catalogo)
        elif option==0:
            break
    option=imprimirMenu()
```
*****

  <a href="https://github.com/bermejo4/Programas-en-Java/blob/master/BuscadorDeGenes.java" target="_blank"> Link for code in GitHub</a>

*****

 <a href="https://github.com/bermejo4/Programas-en-Java/blob/master/BuscadorDeGenes.java" target="_blank"> Link del código en Github</a>

*****


