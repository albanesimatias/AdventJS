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

const boxes = [
  { l: 1, w: 1, h: 1 },
  { l: 3, w: 3, h: 3 },
  { l: 2, w: 2, h: 2 }
]

fitsInOneBox(boxes) // true
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
    let bool = true
    boxes.sort((a,b) => (a.l<=b.l && a.w<=b.w && a.h<=b.h)? 1: -1)
    .reduce((ant,act) => {
        if(ant.l<=act.l || ant.w<=act.w || ant.h<=act.h)
          bool = false
        return act
      },{l:999, h:999, w:999})
      return bool
}
```
