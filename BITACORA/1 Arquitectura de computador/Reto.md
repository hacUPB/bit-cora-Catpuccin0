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
