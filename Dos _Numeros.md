.model small
.stack 100h ; tama?o de la pila
.data ; inicio de la secci?n de datos

u db 0 ; unidades
d db 0 ; decenas
n db 0 ; n?mero completo

mensaje1 db 10,13,7, "Ingrese un numero de dos digitos: $"
mensaje2 db 10,13,7, "Numero ingresado: $"

.code
main proc ; inicio del proceso principal
    ; inicializar el segmento de datos
    mov ax, @data
    mov ds, ax

    ; mostrar mensaje1 "Ingrese un numero de dos digitos"
    mov ah, 09h
    lea dx, mensaje1
    int 21h

    ; leer el primer d?gito (decenas)
    mov ah, 01h
    int 21h
    sub al, 30h ; convertir de ASCII a valor num?rico
    mov d, al   ; guardar en d (decenas)

    ; leer el segundo d?gito (unidades)
    mov ah, 01h
    int 21h
    sub al, 30h ; convertir de ASCII a valor num?rico
    mov u, al   ; guardar en u (unidades)

    ; calcular el n?mero completo: n = (decenas * 10) + unidades
    mov al, d   ; cargar el valor de las decenas
    mov ah, 0   ; limpiar el registro AH
    mov bl, 10  ; multiplicar por 10
    mul bl      ; AL = d * 10
    add al, u   ; sumar las unidades
    mov n, al   ; guardar el n?mero completo en n

    ; mostrar mensaje2 "Numero ingresado: "
    mov ah, 09h
    lea dx, mensaje2
    int 21h

    ; mostrar el n?mero ingresado
    mov al, n
    AAM         ; convertir el valor en AX a ASCII (dividir entre 10)
    mov bx, ax  ; guardar los d?gitos en BX

    ; mostrar el d?gito de las decenas (en BH)
    mov ah, 02h
    mov dl, bh  ; cargar el valor de las decenas en DL
    add dl, 30h ; convertir a ASCII
    int 21h     ; mostrar el d?gito

    ; mostrar el d?gito de las unidades (en BL)
    mov ah, 02h
    mov dl, bl  ; cargar el valor de las unidades en DL
    add dl, 30h ; convertir a ASCII
    int 21h     ; mostrar el d?gito

    ; terminar el programa
    mov ah, 4Ch
    int 21h

main endp
end main
