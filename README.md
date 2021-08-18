<a name="top"></a>
# Proyecto Estructura de Computadores 20/21
Proyecto de Programación en Ensamblador - Estructura de Computadores 2020-2021 UPM ETSIINF

Este proyecto pasa todas las pruebas del corrector de la asignatura para el curso 2020-2021.



> **IMPORTANTE:** Este repositorio pretende servir como ejemplo y ayuda para la realización del Proyecto de ensamblador de la asginatura de Estructura de Computadores. No está permitida la copia de este repositorio, así como la copia de los ficheros fuente y la memoria del proyecto. Copiarlo integramente puede suponer que el sistema de corrección de la asignatura detecte copia y suspenda tu evaluación, por lo que **DEBE HACER SU PROPIO CÓDIGO**.


## Autor

- Erik Trujillo Guzmán





##  Índice

1. [Archivos del repositorio](#apartado1)
2. [Cómo utilizar el simulador](#apartado2)
3. [Casos de prueba](#apartado3)
4. [Observaciones finales](#apartado4)



<a name="apartado1"></a>
## 1. Archivos del repositorio

> **Nota**: Los archivos de este repositorio sirven para correr el simulador en Windows. En caso de que use Linux vaya a la [página de la asignatura](https://www.datsi.fi.upm.es/docencia/Estructura_09/Proyecto_Ensamblador/) y descargue la distribución para Linux.


### 88k_Windows/

Contiene los ficheros fuente del proyecto así como los ejecutables para poder correr el simulador del MC88110.

- **filtror21.ens**: fichero fuente del proyecto. Contiene el código fuente de todas las subrutinas, casos de prueba y programa principal.
- **filtror21.bin**: fichero binario del proyecto.

- **88110e - 88110e.exe**: programa que permite ensamblar un fichero con un programa ensamblador a un fichero binario que puede leer el simulador.

- **em88110 - 88110.exe**: simulador del MC88110.

- **serie**: fichero de configuración de un computador serie sin memorias caché.



### doc/

Contiene la documentación del proyecto.

- **88k_Win_ejemplos/**: directorio con ejemplos en ensamblador.

- **Apuntes_Proyecto.txt**: archivo de texto que contiene un resumen y algunos puntos importantes del proyecto recogidos durante la presentación de este.

- **CasosPrueba_20-21.pdf**: archivo con casos de prueba para todas las subrutinas del proyecto así como un ejemplo de programa principal.

- **Enunciado_Proy_EC_2021.pdf**: enunciado del proyecto, con descripción de las subrutinas, normas de entrega, etc.

- **Instalación.pdf**: archivo que contiene los pasos a seguir para la instalación del simulador del MC88110.

- **Manual de usuario 88110.pdf**: es el manual del MC88110. Contiene información sobre el emulador así como el juego de instrucciones del MC88110.

- **memoria.pdf**: memoria del proyecto. Contiene el historial del proyecto con los avances hechos, los casos de prueba utilizados para testear el el proyecto y un apartado de conclusiones.

- **Presentacion_Proy_EC_2021.pdf**: documento que resume el enunciado del proyecto. Puede tomarse como referencia para codificar, pero no contiene toda la información del enunciado.

- **Pruebas_Corrector.txt**: archivo de texto que contiene todas las pruebas que pasa el corrector de la asignatura al proyecto.


[Back to top](#top)
	
	
<a name="apartado2"></a>
## 2. Cómo utilizar el simulador

Para utilizar el simulador sitúese en el directorio 88k_Windows/ y abra una ventana MS-DOS (CMD).

Para compilar el fichero fuente:

	88110e [-e P_entrada] -o filtror21.bin filtror21.ens
	
La opción *-e* permite especificar un punto de entrada (una etiqueta en el fichero fuente) desde el cual comenzará a ejecutarse el programa.
	
	
Para ejecutar el simulador:

	mc88110.bat filtror21.bin
	

Una vez dentro del simulador puede teclear las siguientes opciones:

- **t \[nº instrucciones\]**: permite pasar a la siguiente instruccón. Si se le añade un número de instrucciones, el simulador avanzará dicho número de instrucciones.

- **v pos_memoria**: muestra el contenido de una posición de memoria escrita en hexadecimal.

- **r reg dato**: guarda un dato en un registro.

- **h**: despliega la ayuda del simulador.

- **q**: se sale del simulador.
	
	
Para más información, puede consultar el [manual](https://github.com/Eriik24/Proyecto-Ensamblador-20-21/blob/main/doc/Manual%20de%20usuario%2088110.pdf).
	
	
[Back to top](#top)



<a name="apartado3"></a>
## 3. Casos de prueba

El fichero ["doc/Pruebas_Corrector.txt"](https://github.com/Eriik24/Proyecto-Ensamblador-20-21/blob/main/doc/Pruebas_Corrector.txt) contiene todas las pruebas que pasa el corrector de la asignatura al proyecto. En el curso 2020-2021 el programa de pruebas constaba de un total de 93 casos de pruebas. Este proyecto pasa todas las pruebas del corrector de la asignatura para dicho curso.


A partir de la línea 520 del fichero fuente del proyecto (["filtror21.ens"](https://github.com/Eriik24/Proyecto-Ensamblador-20-21/blob/main/88k_Windows/filtror21.ens)) se encuentran todos los casos de prueba que utilicé para testear el funcionamiento del proyecto. La explicación de cada prueba se encuentra en el apartado "Juego de ensayo" de la memoria del proyecto (["doc/memoria.pdf"](https://github.com/Eriik24/Proyecto-Ensamblador-20-21/blob/main/doc/memoria.pdf)).

Para codificar una prueba puede hacerlo de la siguiente forma:

```assembly
		;Sqrt1d(0) = 0			;resultado esperado
Sqrt1d_0:	or	r30, r0, 0x9000		;r30 <- pila
		addu	r28, r0, r0
			
		PUSH	(r28)
		bsr	Sqrt1d			;llamada a subrutina
		POP	(r28)
		stop
```
	
Al especificar una etiqueta a cada caso de prueba puede compilar su proyecto utilizando la opción *-e* para ejecutar dicho caso de prueba. Por ejemplo:

	88110e -e Sqrt1d_0 -o filtror21.bin filtror21.ens
	
De esta forma al ejecutar el programa se pondrá en marcha el caso de prueba "Sqrt1d_0".
	
	
[Back to top](#top)


<a name="apartado4"></a>
## 4. Observaciones finales

Aunque cada año el enunciado del proyecto cambia, el 80% del proyecto de este repositorio podrá serle útil para avanzar con el suyo. Tal y como se dijo al principio, ***queda prohibida la copia de este proyecto***, ya que el único propósito es de servir como ejemplo y ayuda para la realización del mismo.

Este proyecto pasa todas las pruebas del corrector de la asignatura para el curso 2020-2021.

Cualquier duda puede preguntarme o dirigirse a la [página de la asignatura](https://www.datsi.fi.upm.es/docencia/Estructura_09/Proyecto_Ensamblador/).

¡Mucha suerte y ánimo! :blush:


[Back to top](#top)
		
