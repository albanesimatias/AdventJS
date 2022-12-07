<h1>Instrucciones</h1>
<p>
Santa Claus necesita hacer una revisión de sus cajas de regalos para asegurarse de que puede empaquetarlas todas en su trineo. Cuenta con una serie de cajas de diferentes tamaños, que se caracterizan por su longitud, anchura y altura.

Tu tarea es escribir una función que, dada una lista de cajas con sus tamaños, determine si es posible empaquetar todas las cajas en una sola de manera que cada caja contenga a otra (que a su vez contenga a otra, y así sucesivamente).

Cada caja representa sus medidas con un objeto. Por ejemplo: {l: 2, w: 3, h: 2}. Esto significa que la caja tiene una longitud de 2, una anchura de 3 y una altura de 2.

Una caja entra en otra caja si todos los lados de la primera son menores a los lados de la segunda. Los elfos nos han dicho que las cajas no se pueden rotar, así que no se puede poner una caja de 2x3x2 en una caja de 3x2x2. Veamos unos ejemplos:
</p>

```js
fitsInOneBox([
  { l: 1, w: 1, h: 1 },
  { l: 2, w: 2, h: 2 }
]) // true

fitsInOneBox([
  { l: 1, w: 1, h: 1 },
  { l: 2, w: 2, h: 2 },
  { l: 3, w: 1, h: 3 }
]) // false

fitsInOneBox([
  { l: 1, w: 1, h: 1 },
  { l: 3, w: 3, h: 3 },
  { l: 2, w: 2, h: 2 }
]) // true
```
<p>
Cosas a tener en cuenta:
<ul>
  <li>Las cajas no se pueden rotar ya que los elfos nos han dicho que la máquina no está preparada.</li>
  <li>Las cajas pueden venir desordenadas de tamaño.</li>
  <li>Las cajas no son siempre cuadradas, pueden ser rectangulares.</li>
</ul>
</p>

<h2>Solucion</h2>

```js
function fitsInOneBox(boxes) {
    let ant = {l:0, h:0, w:0}
    return boxes.sort((a,b) => (a.l+a.w+a.h) - (b.l+b.w+b.h))
    .every(box => {
        if(ant.l>=box.l || ant.w>=box.w || ant.h>=box.h)
          return false
        ant = box
        return true
    })
}
```
