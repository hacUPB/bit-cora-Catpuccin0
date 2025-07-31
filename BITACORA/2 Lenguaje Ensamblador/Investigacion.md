# Lenguaje ensamblador

## Actividad 1
En esta unidad, exploraremos cómo se pueden implementar en lenguaje ensamblador algunos conceptos básicos de programación en alto nivel. Usaremos la plataforma Hack y la CPU Hack para entender cómo se realizan las operaciones de entrada y salida, y cómo se puede manipular la memoria directamente.

### ¿Qué es un computador digital moderno y ¿Cuáles son sus partes?
```
Un computador digital moderno, es aquel que cumple con varias funciones, entre esas diferencio 4 componentes importantes.
- La recolecta de datos
- El procesamiento de información (CPU, "funciona como un cerebro")
- Almacenamiento de datos (RAM "guarda la información como una biblioteca temporalmente")
- Comunica el resultado
```
¿Qué es la entrada-salida mapeada a memoria? 
```
La entrada-salida mapeada a memoria es cuando los dispositivos de entrada y salida, como el teclado y la pantalla, se asignan a direcciones de memoria específicas. Esto permite que el procesador los controle directamente leyendo o escribiendo en esas direcciones de memoria.
```
¿Cómo se implementa en la plataforma Hack?
```
En Hack, la entrada-salida mapeada a memoria se implementa asignando direcciones de memoria específicas a los dispositivos. Por ejemplo, a partir de la dirección 16384 se controla la pantalla, y hay una dirección fija para leer el estado del teclado.
```
- Inventa un programa que haga uso de la entrada-salida mapeada a memoria.
- Investiga el funcionamiento del programa con el simulador.
```
  // Programa en Hack para encender la pantalla si se presiona la tecla 'A'

@24576       // Dirección de memoria del teclado
D=M          // Leer el valor de la tecla presionada en D
@65          // Código ASCII de la tecla 'A'
D=D-A        // Comparar si la tecla presionada es 'A'
@FIN         // Si no es 'A', saltar al final
D;JNE        // Salta a FIN si la comparación no es cero (A no presionada)

@16384       // Dirección de inicio de la pantalla
M=-1         // Enciende el primer píxel de la pantalla
@16385       // Siguiente dirección de la pantalla
M=-1         // Enciende el segundo píxel (opcional, para mostrar más)
@16386       // Más direcciones de la pantalla (opcional)
M=-1         // Enciende el tercer píxel (y así sucesivamente)

@FIN         // Instrucción infinita para detener el programa
0;JMP
```

## Actividad 2
Ya lo analice y lo comprendi dentro de lo que cabe.

## Actividad 3
Vas a implementar y simular una modificación al retos 20 de la unidad anterior. Si se presiona la letra “d” muestras la imagen que diseñaste en el reto 18. Si no se presiona ninguna tecla, borraras la imagen.
