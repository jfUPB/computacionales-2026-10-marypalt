# Unidad 1

## Bitácora de aplicación 
### ACTIVIDAD 4
Implementando un ciclo simple
Crea un programa que use un ciclo para sumar los números del 1 al 5 y guarde el resultado en la dirección de memoria 12.
```asm
@5
D=A
@13
M=D        // RAM[13] = 5  (contador)

@0
D=A
@12
M=D        // RAM[12] = 0  (suma)

(LOOP)
@13
D=M
@END
D;JEQ

@12
M=M+D

@13
M=M-1

@LOOP
0;JMP

(END)
@END
0;JMP
```
<img width="1105" height="401" alt="image" src="https://github.com/user-attachments/assets/7bb6d9b5-7616-4e47-9d9f-849ea1232a89" />

## Bitácora de reflexión
### ACTIVIDAD 5
1. El Program Counter se encarga de indicar el número de la instrucción o paso en el que se encuentra el programa, es decir, va numerando las lineas que lee.
2. Este carga el número en el registro A, indica una variable para saber qué guarda en la memoria o una etiqueta. En cambio, la instrucción C es la de trabajo, resuelve las instrucciones y variables indicadas (Cálculos, escribir en memoria, saltos y mover datos). 





