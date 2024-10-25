CR EQU 13;

LF EQU 10


Datos Segment

   LINEA1 DB CR,LF,'Anel Gomez Vidal' ,CR,LF,'$'
   LINEA2 DB 'Tecnologico de Estudios Superiores de Jilotepec' ,CR,LF,'$'
   LINEA3 DB 'ING.SISTEMAS COMPUTACIONALES' ,CR,LF,'$'
   LINEA4 DB 'ANE ;-;' ,CR,LF,'$'
       
    
 Datos ENDS
 
 
 
Pila Segment Stack

  db 64 DUP('Pila')
  
  Pila Ends
  
  
  
  Codigo Segment
  
  LN proc far
    Assume CS:Codigo, DS:Datos, SS:Pila
     mov ax, Datos
      mov ds,ax 
      lea DX,LINEA1
      call Escribe
      lea DX,LINEA2
      call Escribe
      lea DX,LINEA3
      call Escribe
      lea DX,LINEA4
      call Escribe
       mov ax, 4c00h
       int 21h
       LN ENDP
 Escribe proc
      mov ah,9
      int 21h
      ret
      
      
Escribe endp

Codigo Ends

End LN      
