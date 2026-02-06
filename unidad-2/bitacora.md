# Unidad 2

## Bitácora de proceso de aprendizaje
### Actividad 1 
<img width="162" height="187" alt="image" src="https://github.com/user-attachments/assets/5fda2679-aa81-4be8-80bd-3754c47cfafc" />

### Actividad 2
<img width="131" height="181" alt="image" src="https://github.com/user-attachments/assets/82605e97-4499-4eb9-99a6-3048aa5d0d94" />

### Actividad 3
<img width="509" height="522" alt="image" src="https://github.com/user-attachments/assets/f734c1b1-3c79-475e-a220-8c8474ee32f9" />
Fotos del código en el celular, copiar en el ensamblador y tomarle captura. (Ref: 4 Feb)

## Bitácora de aplicación 
### Actividad 5 
#### Traducción 1 a Assembler
<img width="465" height="493" alt="image" src="https://github.com/user-attachments/assets/fd7cdab8-6b68-4541-b12c-9d18c625c9fb" />
#### Traducción 1 a Assembler
````asm
// int a = 10;

@10
D=A
@a
M=D
// int b = 5;

@5
D=A
@b
M=D
// int *p;
// p = &a;

@a 
D=A 
@p
M=D
// b = *p;

@p
A=M // A = 16
D=M // D = contenido de la dirección 16 --> 10
@b // se guarda en a la dirección de b --> 17
M=D // Guardando en la 17 (que es b), el 10 que tengo en D
````


## Bitácora de reflexión



