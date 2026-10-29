# Ticket de salida 3

Nombre: Ignacio Bastías

Rol: 202179025-k

Link al repositorio de GitHub (extra):

## Errores

### Error 1
- Tipo de error: Invalid read of size 4
- Línea del código:Linea 20
- Corrección:for(int i = 0; i < f-1; i++) en la linea 20

### Error 2
- Tipo de error: Invalid write of size 4
- Línea del código: 71
- Corrección: for(int i = 0; i < f-1; i++) en la linea 70

### Error 3
- Tipo de error:72 (24 direct, 48 indirect) bytes in 1 blocks are definitely lost in loss record 2 of 2
- Línea del código: Linea 6
- Corrección:    for(int i = 0; i < f; i++){
        free(caja[i]);
    }
    free(caja); 
    linea 95

### Error 4
- Tipo de error:
- Línea del código:
- Corrección:

## Caso de prueba propio (case_04)

Explicación: no hay filas ni columnas
pero la compra cuesta 0 por lo que si compra
