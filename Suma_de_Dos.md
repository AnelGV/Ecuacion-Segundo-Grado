.model small
.stack 100h
.data
    num1 db 0
    num2 db 0
    num3 db 0

    mensaje1 db 10,13,7, "Primer numero:", "$"
    mensaje2 db 10,13,7, "Segundo numero:", "$"
    mensaje3 db 10,13,7, "La suma es:", "$"

.code
main proc
    mov ax, @data
    mov ds, ax

    ; Mostrar el primer mensaje
    mov ah, 09h
    lea dx, mensaje1
    int 21h

    ; Leer el primer n?mero
    mov ah, 01h
    int 21h
    sub al, 30h       ; Convertir el car?cter a n?mero
    mov num1, al

    ; Mostrar el segundo mensaje
    mov ah, 09h
    lea dx, mensaje2
    int 21h

    ; Leer el segundo n?mero
    mov ah, 01h
    int 21h
    sub al, 30h       ; Convertir el car?cter a n?mero
    mov num2, al

    ; Sumar los dos n?meros
    mov al, num1
    add al, num2
    mov num3, al      ; Guardar el resultado de la suma en num3

    ; Mostrar el mensaje de resultado
    mov ah, 09h
    lea dx, mensaje3
    int 21h

    ; Convertir el resultado a car?cter para mostrarlo
    add num3, 30h     ; Convertir el n?mero a car?cter ASCII
    mov dl, num3
    mov ah, 02h
    int 21h           ; Mostrar el resultado

    ; Terminar el programa
    mov ax, 4C00h
    int 21h
main endp
end main
