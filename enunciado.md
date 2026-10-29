# Ordenando monedas

Después de estar tanto tiempo teniendo que mirar árboles de mandarinas se aburrió. Tomó un giro en 360 grados y decidió dedicarse a algo más tranquilo. Ahora ordena monedas que fue juntando con el paso del tiempo. 

Estas las guarda en una caja con separaciones de $F$ filas y $C$ columnas, donde cabe una moneda por espacio. Existen todo tipo de monedas, de \$500, \$100, \$1, etc.

Una amiga, que está más metida en este mundo de ordenar monedas, le pasó un programa, `monedas.c`, que fue creado para revisar una caja de monedas. Este revisa cuánta plata hay en cada fila, si la caja está ordenada y hasta qué fila tiene que sacar monedas para pagar alguna compra.

Usted hace unos casos de prueba que entregan los resultados esperados, pero de todas maneras, quiere verificar por su cuenta el código para no llevarse alguna sorpresa con la gestión de su dinero, por lo que decide revisarlo con valgrind.

Además usted sabe que:
- Una fila es de **monedas grandes** si tiene monedas y el promedio de sus monedas (con división entera) es de al menos \$100.
- La caja está **ordenada** si cada fila tiene al menos tanta plata como la siguiente.
- Para revisar si puede **pagar una compra** saca **todas** las monedas de la fila 1, después las de la fila 2, y así hasta juntar el precio. Cada compra se revisa con la caja completa, no se descuentan las monedas al hacer una revisión.

## Entrada

La primera línea contiene la cantidad de filas y de columnas de la caja, $1 \leq F, C \leq 10$.

Le siguen $F$ líneas con $C$ enteros cada una: 0 si el espacio está vacío, o el valor de la moneda (1, 5, 10, 50, 100 o 500).

Luego viene una línea con la cantidad de compras $1 \leq Q \leq 10$ y una línea con los $Q$ precios (1 a 50000).

## Salida

Imprime:

1. Una línea por fila: `Fila i: $P (K monedas)`, con la plata que hay en la fila y cuántas monedas tiene.
2. `Filas de monedas grandes: N`.
3. `Caja ordenada: Si` o `Caja ordenada: No`.
4. Una línea por compra: `Compra j: hasta la fila i`, con la primera fila con la que se junta el precio, o `Compra j: no alcanza` si no se junta ni con toda la caja.

## Qué hacer

El programa tiene **4 errores de memoria**.

1. Compruebe con `probar.sh` que el programa entrega la salida esperada en los tres casos.
2. Revise el programa con valgrind. La línea para hacerlo está comentada en `probar.sh`.
3. Corrija un error a la vez y vuelva a ejecutar valgrind después de cada corrección. **Por cada error, complete en el `README.md`**:
    - Tipo de error que reporta valgrind
    - Línea del código donde está
    - Corrección.
4. Cree el caso de prueba `testCases/case_04.in`, con su respuesta en `case_04.ans`, en el que **una de las compras cueste exactamente toda la plata de la caja**. En el `README.md`, explique cómo se llega a esa respuesta, de manera similar al ejemplo de abajo.

El código estará arreglado cuando valgrind diga, en los cuatro casos, que no hay ningún error y que todos los bloques fueron liberados, y la salida siga siendo la esperada.

## Entrega

Suba a AULA un `.zip` con `monedas.c` corregido, el `README.md` completo y los archivos `case_04.in` y `case_04.ans`.

**Extra (+20 puntos para un ticket de salida):** suba la carpeta del ticket al repositorio de GitHub que creó en el laboratorio pasado y ponga el link en el `README.md`. Sólo válido si el repositorio fue creado el miércoles pasado.

## Ejemplo

### Entrada
```
3 4
500 100 0 50
100 100 10 0
5 1 0 10
2
600 700
```
### Salida
```
Fila 1: $650 (3 monedas)
Fila 2: $210 (3 monedas)
Fila 3: $16 (3 monedas)
Filas de monedas grandes: 1
Caja ordenada: Si
Compra 1: hasta la fila 1
Compra 2: hasta la fila 2
```
### Explicación
```
Fila 1: 500 + 100 + 50 = 650 en 3 monedas, promedio 216: de monedas grandes
Fila 2: 100 + 100 + 10 = 210 en 3 monedas, promedio 70
Fila 3: 5 + 1 + 10     = 16 en 3 monedas, promedio 5
650 >= 210 >= 16, asi que la caja esta ordenada
Compra 1 ($600): con la fila 1 ya se juntan $650
Compra 2 ($700): con la fila 1 no alcanza; con las filas 1 y 2 se juntan $860
```
