# Instrucciones
<p>
Una pareja está poniendo el árbol de navidad. El chico es un motivado de los adornos navideños y quiere que quede perfectamente equilibrado. Tiene tres tipos de decoraciones:
 ° Bolas de colores : B
 ° Regalos pequeños : R
 ° Piñas de pino : P
El árbol de navidad es un triángulo que hay que generar. Ya tienen la base montada, que sería la primera fila, y a partir de ahí tienen que ir colocando las decoraciones hacía arriba siguiendo una fórmula.
</p>

```js
Arriba coloca  :     P     R     B     P
Si abajo tiene :    P P   B P   R P   B R
```
<p>
Las combinaciones también son al revés. Por ejemplo, si abajo es B P, arriba es R. Pero también será R si abajo es P B. También si abajo tienes dos veces la misma letra, arriba será la misma letra. Por ejemplo, si abajo es B B, arriba es B.

Con estas reglas, podríamos ver el árbol que generaríamos con la base B P R P:
</p>

```js
   R
  P B
 R B B
B P R P
```

<p>Escribe un programa que reciba el string B P R P y devuelva un array con la representación del árbol.</p>

```js
decorateTree('B P R P')
// [
// 'R',
// 'P B',
// 'R B B',
// 'B P R P'
// ]

decorateTree('B B') // ['B', 'B B']
```

<h3>Ten en cuenta que:</h3>
<ul>
  <li>El programa recibe siempre la cadena de texto que representa la base del árbol.</li>
  <li>Hay que generar el árbol completo, es decir, la base y las filas que se generan a partir de ella, hasta arriba.</li>
  <li>Hay que seguir la fórmula para saber qué decoración colocar en cada posición.</li>
<ul>

<h2>Solución</h2>  
  
```js
function decorateTree(base) {
  const rules = {
                 'PP': 'P','BB': 'B','RR': 'R',
                 'BP': 'R','RP': 'B','BR': 'P',
                 'PB': 'R','PR': 'B','RB': 'P',
                }
  const decorate = [base]
  base = base.split(' ')
  while (base.length > 1) {
    base = base.slice(1).map((x, i,) => rules[base[i]+x])
    decorate.unshift(base.join(' '))
  }
  return decorate
}
```
