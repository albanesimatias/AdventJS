# Instrucciones

<p>
El día se acerca y Papá Noel tiene el almacén de juguetes hecho un desastre. Ayúdale a ordenar los juguetes en el almacén para que pueda encontrarlos más fácilmente.

Para ello, nos dan dos arrays. El primero es un array de juguetes, y el segundo es un array de números que indican la posición de cada juguete en el almacén.

Lo único a tener en cuenta es que las posiciones pueden no empezar en 0, aunque siempre serán números consecutivos y de forma ascendente.

Tenemos que devolver un array donde cada juguete esté en la posición que le corresponde.
</p>

```js
const toys = ['ball', 'doll', 'car', 'puzzle']
const positions = [2, 3, 1, 0]

sortToys(toys, positions)
// ['puzzle', 'car', 'ball', 'doll']

const moreToys = ['pc', 'xbox', 'ps4', 'switch', 'nintendo']
const morePositions = [8, 6, 5, 7, 9]

sortToys(moreToys, morePositions)
// ['ps4', 'xbox', 'switch', 'pc', 'nintendo']
```

<h3>A tener en cuenta</h3>
<ul>
  <li>Siempre habrá el mismo número de juguetes que de posiciones.</li>
  <li>Ni los juguetes ni las posiciones se repiten.</li>
</ul>

<h2>Solucion</h2>
  
 ```js
 function sortToys(toys, positions) {
  const orderPos = [...positions].sort((a,b)=>a-b)
  const orderToys = []
  orderPos.forEach((x)=>{
    orderToys.push(toys[positions.indexOf(x)])
  })
  return orderToys
} 
 ```
