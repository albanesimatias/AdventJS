# Instrucciones
<p>
Hay muchas cartas de niños pidiendo regalos y es muy difícil que podamos hacer inventario de todos ellos. Por eso, hemos decidido crear un programa que nos dibuje una tabla con los regalos que nos piden y sus cantidades.

Para ello nos dan un array de objetos con los nombres de los regalos y sus cantidades. Escribe una función que reciba este array y devuelva una cadena con la tabla dibujada.
</p>

```js
printTable([
  { name: 'Game', quantity: 2 },
  { name: 'Bike', quantity: 1 },
  { name: 'Book', quantity: 3 }
])
+++++++++++++++++++
| Gift | Quantity |
| ---- | -------- |
| Game | 2        |
| Bike | 1        |
| Book | 3        |
*******************
```

<p>
Otro ejemplo donde se puede ver que la tabla siempre usa sólo el espacio justo dependiendo de la longitud de los nombres de los regalos y de las cantidades.
</p>

```js
printTable([
  { name: 'PlayStation 5', quantity: 9234782374892 },
  { name: 'Book Learn Web Dev', quantity: 23531 }
])
++++++++++++++++++++++++++++++++++++++
| Gift               | Quantity      |
| ------------------ | ------------- |
| PlayStation 5      | 9234782374892 |
| Book Learn Web Dev | 23531         |
**************************************
```

<p>
Como ves, el tamaño de las celdas depende de la longitud de los nombres de los regalos y de las cantidades, aunque como mínimo tendrán que ser del espacio de los títulos Gift y Quantity respectivamente.

La tabla usa los símbolos: + para el borde superior, * para el borde inferior, - para las líneas horizontales y | para las líneas verticales.
</p>

<h3>Ten en cuenta:</h3>
<ul>
  <li>Usa sólo el espacio que necesitas para dibujar la tabla.</li>
  <li>Adapta la tabla a la longitud de los nombres de los regalos y de las cantidades o los títulos de las columnas.</li>
  <li>No hace falta que ordenes los resultados.</li>
  <li>La tabla no termina con salto de línea.</li>
</ul>

<h2>Solución</h2>

```js
function printTable(gifts) {
  const maxGl = Math.max(...gifts.map(g => g.name.length), 4)
  const maxQl = Math.max(...gifts.map(g => `${g.quantity}`.length), 8)
  const totalL = maxGl + maxQl + 7

  const top = '+'.repeat(totalL) + '\n'
  const bottom = '*'.repeat(totalL)
  const header = '| Gift'+' '.repeat(maxGl-4) +
                ' | Quantity '+' '.repeat(maxQl-8) + '|\n'
  const div = `| ${'-'.repeat(maxGl)} | ${'-'.repeat(maxQl)} |\n`
  let rows = gifts.reduce((row,g) => row + '| ' + g.name +
    ' '.repeat(maxGl - g.name.length) + ' | ' + g.quantity +
    ' '.repeat(maxQl - `${g.quantity}`.length) + ' |\n'
  ,'')
  return top + header + div + rows + bottom
}
```
