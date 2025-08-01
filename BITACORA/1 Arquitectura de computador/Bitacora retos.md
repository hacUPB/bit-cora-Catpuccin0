### Retos!

1. Carga en D el valor 1978.
```
 @1978
 D=A
```

2. Guarda en la posición 100 de la RAM el número 69.
```
@69
A=D
@100
M=D
```

3. Guardado en la posición 200 de la RAM el contenido de la posición 24 de la RAM: Copia el valor almacenado en la posición 24 de la RAM a la posición 200
```
@24
D=A
D=M
@200
M=D
```

4. Lee lo que hay en la posición 100 de la RAM, resta 15 y guarda el resultado en la posición 100 de la RAM
```
@15
D=A
@100
M=M-D
```

5. Suma el contenido de la posición 0 de la RAM, el contenido de la posición 1 de la RAM y con la constante 69. Guarda el resultado en la posición 2 de la RAM.
```
@0
D=A
D=M
@1
D=D+M
@69
D=D+A
@2
M=D 
```

6. Si el valor almacenado en D es igual a 0 salta a la posición 100 de la ROM.
```
@100
D;JEQ
```

7. Si el valor almacenado en la posición 100 de la RAM es menor a 100 salta a la posición 20 de la ROM.
```
@100
D=M
D=D-A
@20
D;JLT
```

8. Considera el siguiente programa:
```
@var1
D = M
@var2
D = D + M
@var3
M = D
```
- ¿Qué hace este programa?
```
Este lo programa lo que está haciendo es ir a la posición 16 y 17 que serian las variables var1 y var2 respectivamente, sumando los datos que estos almacenan y guardando el resultado en la variable 3, osea, posición 18. 
```
- En qué posición de la memoria está var1, var2 y var3? ¿Por qué en esas posiciones?
```
Estan en las posiciones 16,17,18 por que las anteriores a estas están almacenadas para datos de la computadora.
```

9. Considera el siguiente programa:
```
i = 1
sum = 0
sum = sum + i
i = i + 1
```
La traducción a lenguaje ensamblador del programa anterior es:
```
// i = 1
@i
M=1
// sum = 0
@sum
M=0
// sum = sum + i
@i
D=M
@sum
M=D+M
// i = i + 1
@i
D=M+1
@i
M=D
```
- ¿Qué hace este programa?
```
Este programa lo que está haciendo es almacenar un numero en la variable "i" y otro en la variable "sum", luego, daba un nuevo valor a la variable donde almacenamos el numero i, osea en "sum" con la suma de su valor anterior y el valor de la variable "i", y luego estaba dando a "i" el valor de la "sum" de su dato anterior mas 1.
```
 
- ¿En qué parte de la memoria RAM está la variable `i` y `sum`? ¿Por qué en esas posiciones?
```
Están en la posición 16 y 17, porque automitamente organiza las variables en el orden que aparezcan apartir de los espacios que tiene disponibles para usar, osea, apartir del 16, debido a que del 15 para abajo son reservadas para el computador segun el curso de NAND TETRIS.
```
 
- Optimiza esta parte del código para que use solo dos instrucciones:
```
// i = i + 1
@i
D=M+1
@i
M=D
```
Segun lo que yo veo la posible forma de optimizarlo seria:
```
@i 
M=M+1
```

10. Las posiciones de memoria RAM de 0 a 15 tienen los nombres simbólico R0 a R15. Escribe un programa en lenguaje ensamblador que guarde en R1 la operación 2 * R0.
```
@R0
D=M
D=D+M
@R1
M=D
```

11. Considera el siguiente programa:
```
i = 1000
LOOP:
if (i == 0) goto CONT
i = i - 1
goto LOOP
CONT:
```
La traducción a lenguaje ensamblador del programa anterior es:
```
// i = 1000
@1000
D=A
@i
M=D
(LOOP)
// if (i == 0) goto CONT
@i
D=M
@CONT
D;JEQ
// i = i - 1
@i
M=M-1
// goto LOOP
@LOOP
0;JMP
(CONT)
```

1- ¿Qué hace este programa?

Este programa lo que está haciendo es identificar un valor, donde "i" es igual a 0 puede saltarse el loop, pero sino, debe de continuarlo, donde por cada vez que pase se le resta un numero y asi hasta que cumpla con la condición para poder continuar. Es un tipo bucle que empieza con la variable "i" igual a 1000 y la disminuye en 1 en cada iteración. El bucle continúa hasta que el valor de "i" llega a 0. Una vez que "i" es 0, el programa salta a la etiqueta CONT, que marca el final del bucle

2- ¿En qué memoria está almacenada la variable i? ¿En qué dirección de esa memoria?

Esta en la memoria RAM y ocupada la pisicón 16. Si "i" es la primera variable declarada en el programa, se le asigna la primera dirección disponible.
 
3- ¿En qué memoria y en qué dirección de memoria está almacenado el comentario //`i = 1000?`

No ocupa ningun espacio dentro de la memoria debido a que no se le marca con el codigo, solo es una indicación para el programa que tiene como indicativo de empezar el conteo hacia atras desde el valor 1000
 
4- ¿Cuál es la primera instrucción del programa anterior? ¿En qué memoria y en qué dirección de memoria está almacenada esa instrucción?

La primera instrucción del programa es el valor @1000, las instrucciones se almacenan en la memoria de instrucciones (ROM), que es diferente de la memoria de datos que lee, la cual es (RAM). Así está en la posición 0 de la ROM.
 
5- ¿Qué son CONT y LOOP?

CONT: Es la etiqueta que indica donde debe continuar el programa luego de haber salido del bucle
LOOP: Es la etiqueta que marca el inicio del LOOP, o yo le digo bucle, indicando al programa hasta donde debe regresar para repetirlo
  
6- ¿Cuál es la diferencia entre los símbolos `i` y `CONT`?

"i" es una variable en la RAM, mientras que el CONT es una etiqueta, que no guarda datos, solo marca las posiciones que debe de seguir el codigo. "i" es para continuar el flujo de CONT

12. Implemente en ensamblador:
```
  R4 = R1 + R2 + 69
```
seria: 
```
@R1
D=M
@R2
D=D+M
@69
D=D+M
@R4
M=D
```

13. Implementa en ensamblador: 
```
if R0 >= 0 then R1 = 1
else R1 = –1
(LOOP)
goto LOOP
```

En lenguaje de ensamblador: 
```
(LOOP)
@R1
D=M
@POS
D;JGE
@R1
M=-1
(POS)
@R1
M=1
@LOOP
0;JMP
```

14. Implementa en ensamblador:
```
R4 = RAM[R1]
```

En lengua de ensamblador: 
```
@R1
D=M
@R4
M=D
```

15. Implementa en ensamblador el siguiente problema. En la posición R0 está almacenada la dirección inicial de una región de memoria. En la posición R1 está almacenado el tamaño de la región de memoria. Almacena un -1 en esa región de memoria
```
@R0
A=M
M=-1
@R0
M=M+1
@R1
M=M-1
D=M
@0
D;JGT
```

16. Implementa en lenguaje ensamblador el siguiente programa:
```
int[] arr = new int[10];
int sum = 0;
for (int j = 0; j < 10; j++) {
sum = sum + arr[j];
}
```
en lenguaje ensamblador seria:
```
@R10
D=A
@R1
M=D
@16
D=A
@R0
M=D
(LOOP)
@R2
D=M
@R0
A=M
M=D
@R0
D=M
@R0
M=D+1
@R1
D=M
M=D-1
@R3
D=M
@R2
D=D+M
M=D
@R1
D=M
@LOOP
D;JGT
```

1 - ¿Qué hace este programa?
```
Declara un arreglo de enteros (arr) de tamaño 10. Este programa lo que hace es sumar un numero con el dato anterior en un arreglo de 10 direcciones.
  ```
2 - ¿Cuál es la dirección base de arr en la memoria RAM?
```
Es la posición 16, ya que no se usa desde el 0 al 15.
  ```
3 - ¿Cuál es la dirección base de sum en la memoria RAM y por qué?
```
Usa un ciclo for para recorrer los 10 elementos del arreglo. En la posición 26 ya que es la siguiente libre despues de los 10 espacios del arreglo.
  ```
4 - ¿Cuál es la dirección base de j en la memoria RAM y por qué?
```
Controlando el bucle llevando a la posicion, lo puedo decir que la variable "j" es una variable local que se utiliza dentro del ciclo for como contador. En Java, todas las variables locales se almacenan en una parte de la memoria llamada stack (pila), que se usa para guardar datos temporales durante la ejecución de métodos. Por lo tanto, la dirección base de j se encuentra en el stack.
```

17. Implementa en lenguaje ensamblador:
```
if ( (D - 7) == 0) goto a la instrucción en ROM[69]
```

NOTA: El "goto" salta a la parte del código marcada con una etiqueta. "goto" sirve para saltar a otra parte del programa y continuar desde ahí.
En ensamblador seria: 
```
@R0
D=M
@7
D=D-A
@69
D;JEQ
```

18. Utiliza esta herramienta para dibujar un bitmap en la pantalla. image Link: https://nand2tetris.github.io/web-ide/bitmap
<img width="1441" height="837" alt="image" src="https://github.com/user-attachments/assets/97e1ef1b-370f-44b9-8fd6-5fd77292a691" />

```
function void draw(int location) {
	var int memAddress; 
	let memAddress = 16384+location;
	// column 0
	do Memory.poke(memAddress, 240);
	do Memory.poke(memAddress +32, 264);
	do Memory.poke(memAddress +64, 516);
	do Memory.poke(memAddress +96, -31742);
	do Memory.poke(memAddress +128, 18434);
	do Memory.poke(memAddress +160, 12289);
	do Memory.poke(memAddress +192, 1);
	do Memory.poke(memAddress +224, 1);
	do Memory.poke(memAddress +256, 1);
	do Memory.poke(memAddress +288, 1);
	do Memory.poke(memAddress +320, 2);
	do Memory.poke(memAddress +352, 2);
	do Memory.poke(memAddress +384, 4);
	do Memory.poke(memAddress +416, 8);
	do Memory.poke(memAddress +448, 16);
	do Memory.poke(memAddress +480, 32);
	do Memory.poke(memAddress +512, 64);
	do Memory.poke(memAddress +544, 128);
	do Memory.poke(memAddress +576, 256);
	do Memory.poke(memAddress +608, 512);
	do Memory.poke(memAddress +640, -31744);
	do Memory.poke(memAddress +672, 18432);
	do Memory.poke(memAddress +704, 12288);
	// column 1
	do Memory.poke(memAddress +1, 60);
	do Memory.poke(memAddress +33, 66);
	do Memory.poke(memAddress +65, 129);
	do Memory.poke(memAddress +97, 256);
	do Memory.poke(memAddress +129, 256);
	do Memory.poke(memAddress +161, 512);
	do Memory.poke(memAddress +193, 512);
	do Memory.poke(memAddress +225, 512);
	do Memory.poke(memAddress +257, 512);
	do Memory.poke(memAddress +289, 512);
	do Memory.poke(memAddress +321, 256);
	do Memory.poke(memAddress +353, 256);
	do Memory.poke(memAddress +385, 128);
	do Memory.poke(memAddress +417, 64);
	do Memory.poke(memAddress +449, 32);
	do Memory.poke(memAddress +481, 16);
	do Memory.poke(memAddress +513, 8);
	do Memory.poke(memAddress +545, 4);
	do Memory.poke(memAddress +577, 2);
	do Memory.poke(memAddress +609, 1);
	return;
}
```

19. Analiza el siguiente programa en lenguaje de máquina:
```
0100000000000000
1110110000010000
0000000000010000
1110001100001000
0110000000000000
1111110000010000
0000000000010011
1110001100000101
0000000000010000
1111110000010000
0100000000000000
1110010011010000
0000000000000100
1110001100000110
0000000000010000
1111110010101000
1110101010001000
0000000000000100
1110101010000111
0000000000010000
1111110000010000
0110000000000000
1110010011010000
0000000000000100
1110001100000011
0000000000010000
1111110000100000
1110111010001000
0000000000010000
1111110111001000
0000000000000100
1110101010000111
```

Analizando el codigo en lenguaje ensamblador, seria:
```
@16384   // Dirección base de la pantalla
D=A      // D = 16384
@16      // Usaremos RAM[16] como puntero temporal
M=D      // RAM[16] = 16384
@24576   // Dirección del teclado
D=M      // D = valor del teclado
@19      // Comparamos con RAM[19]
D;JNE    // Si D ≠ RAM[19], continua; si son iguales, salta la sección siguiente
```
Lee la entrada del teclado y compara con un valor almacenado en RAM, en el espacio 19. Si son iguales, el salto se ejecuta (y se omite el siguiente bloque). Si son diferentes, el programa continúa con la siguiente sección.
```
@16
D=M      // D = RAM[16]
@16384
D=D-A    // D = RAM[16] - 16384
@4
D;JLE    // Si D ≤ 0, salta a línea 4 (inicio del ciclo principal)
@16
AM=M-1   // RAM[16]--; A = RAM[16]
M=0      // Borra la celda apuntada (RAM[A] = 0)
@4
0;JMP    // Salta al inicio del ciclo principal
@16
D=M      // D = RAM[16]
@24576
D=D-A    // D = RAM[16] - Teclado
@4
D;JGE    // Si D ≥ 0, vuelve al inicio del ciclo
@16
A=M      // A = RAM[16] (accede a dirección apuntada)
M=-1     // Enciende píxel (RAM[A] = -1)
@16
M=M+1    // Avanza puntero: RAM[16]++
@4
0;JMP    // Regresa al inicio del ciclo
```	
Si se detecta cambio en la entrada del teclado:
1 - Puede borrar píxeles (poner 0) si el puntero va hacia atrás.
2 - Puede encender píxeles (poner -1) si va hacia adelante.

20. Implementa un programa en lenguaje ensamblador que dibuje el bitmap que diseñaste en la pantalla solo si se presiona la tecla “d”.
Codigo del jack:

```
function void draw(int location) {
	var int memAddress;
	let memAddress = 16384 + location;
	do Memory.poke(memAddress + 0, 0);
	do Memory.poke(memAddress + 32, 0);
	do Memory.poke(memAddress + 64, 528);
	do Memory.poke(memAddress + 96, 1848);
	do Memory.poke(memAddress + 128, 4092);
	do Memory.poke(memAddress + 160, 4092);
	do Memory.poke(memAddress + 192, 4092);
	do Memory.poke(memAddress + 224, 2040);
	do Memory.poke(memAddress + 256, 1008);
	do Memory.poke(memAddress + 288, 480);
	do Memory.poke(memAddress + 320, 192);
	do Memory.poke(memAddress + 352, 0);
	do Memory.poke(memAddress + 384, 0);
	do Memory.poke(memAddress + 416, 0);
	do Memory.poke(memAddress + 448, 0);
	do Memory.poke(memAddress + 480, 0);
	return;
}
```

### Debido a inconvenientes con el programa y tambien con mi diseño inicial tuve que reducir el tamaño del corazon pero despues pude hacerle un diseño identico pero mas pequeño pude solucionarlo:
```
(LOOP)
    @24576
    D=M
    @100
    D=D-A
    @DRAW
    D;JEQ
    @LOOP
    0;JMP

(DRAW)
    @16384
    D=A
    @R13
    M=D
    @0
    D=A
    @R13
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @32
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @528
    D=A
    @R13
    D=M
    @64
    D=D+A
    @R14
    M=D
    @528
    D=A
    @R14
    A=M
    M=D
    @1848
    D=A
    @R13
    D=M
    @96
    D=D+A
    @R14
    M=D
    @1848
    D=A
    @R14
    A=M
    M=D
    @4092
    D=A
    @R13
    D=M
    @128
    D=D+A
    @R14
    M=D
    @4092
    D=A
    @R14
    A=M
    M=D
    @4092
    D=A
    @R13
    D=M
    @160
    D=D+A
    @R14
    M=D
    @4092
    D=A
    @R14
    A=M
    M=D
    @4092
    D=A
    @R13
    D=M
    @192
    D=D+A
    @R14
    M=D
    @4092
    D=A
    @R14
    A=M
    M=D
    @2040
    D=A
    @R13
    D=M
    @224
    D=D+A
    @R14
    M=D
    @2040
    D=A
    @R14
    A=M
    M=D
    @1008
    D=A
    @R13
    D=M
    @256
    D=D+A
    @R14
    M=D
    @1008
    D=A
    @R14
    A=M
    M=D
    @480
    D=A
    @R13
    D=M
    @288
    D=D+A
    @R14
    M=D
    @480
    D=A
    @R14
    A=M
    M=D
    @192
    D=A
    @R13
    D=M
    @320
    D=D+A
    @R14
    M=D
    @192
    D=A
    @R14
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @352
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @384
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @416
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @448
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @0
    D=A
    @R13
    D=M
    @480
    D=D+A
    @R14
    M=D
    @0
    D=A
    @R14
    A=M
    M=D
    @END
    0;JMP

(END)
    @END
    0;JMP
```
<img width="1860" height="891" alt="image" src="https://github.com/user-attachments/assets/9dfd7a83-2706-4eb6-a5e8-b1e1718d5a2e" />

### Objetivo cumplido:
Implementar un programa en lenguaje ensamblador Hack que monitoree la entrada del teclado,  la tecla "d" y, al detectar el valor 100, dibuje una figura en la memoria de video, en mi caso fue un corazon.
-------
### Es un bucle de espera (LOOP)
- El programa entra en un bucle infinito monitoreando la dirección "24576", que representa el teclado.
- Si se detecta el valor "100", se salta a la rutina (DRAW).

### Rutina de dibujo (DRAW)
- Se usa la dirección base "16384"  para comenzar a dibujar.
- Con ayuda de los registros temporales "R13" y "R14", se calculan direcciones específicas en memoria.
- En cada posición calculada, se escribe un valor distinto de cero para encender píxeles específicos.
- La figura final corresponde a una forma diseñada manualmente con valores codificados.

### Aprendizaje
- Comprendi el funcionamiento de la memoria de pantalla y de teclado en el sistema Hack junto con el simulador NAND.
- Se que se utilizó acceso directo a direcciones de memoria para manipular la dirección "24576".
- Aunque quedo funcional, la solución es quedo muy larga y puede optimizarse con bucles o etiquetas para dibujos más complejos e inclusive para poder simplificar el codigo.

RETOS:
- El diseño que habia hecho al principio no lo leia, entonces opte por hacer el mismo pero mas pequeño para asi poder tener un mejor resultado
- En varias ocasiones se me borro el diseño y la pagina se bugeaba y no me permitia seguir el dibujando
- El traducir varias veces diversas cosas del hack al lenguaje emulador me confundi y mas al hacer un diseño se repetian muchas partes del codigo sin tener que cambiar la posicion.

## 📁 Archivos entregados

- "reto20.asm": código fuente ensamblador.
- "bitacora retos.md": archivo explicativo de esta solución.

