# Instrucciones
<p>
Estamos preparando los sacos para los regalos de Navidad pero cada saco tiene un límite de peso.

Nos dan un array con los nombres de los regalos y un número que es el peso máximo que puede llevar cada saco. El peso de cada regalo es la longitud de su nombre.

Escribe una función que agrupe los regalos en sacos y devuelva un array con los nombres de los regalos de cada saco. Para agrupar los regalos, se separan los nombres por espacios (el espacio no cuenta como peso).

¡Pero ojo! Cada saco puede llevar un máximo de peso, y si el peso de los regalos de un saco supera el peso máximo, se debe separar el último regalo del saco y ponerlo en el siguiente saco.
</p>

```js
carryGifts(['game', 'bike', 'book', 'toy'], 10)
// ['game bike', 'book toy']
// en cada saco se puede llevar 10kg
// el primer saco lleva 'game' y 'bike' que pesan 4kg y 4kg
// el segundo saco lleva 'book' y ' toy' que pesan 4kg y 3kg

carryGifts(['game', 'bike', 'book', 'toy'], 7)
// ['game', 'bike', 'book toy']
// en cada saco se puede llevar 7kg
// el primer saco sólo puede llevar 'game' que pesa 4kg
// el segundo saco sólo puede llevar 'bike' que pesa 4kg
// el tercer saco lleva 'book' y 'toy' que pesan 4kg y 3kg

carryGifts(['game', 'bike', 'book', 'toy'], 4)
// ['game', 'bike', 'book', 'toy']
// en cada saco se puede llevar 4kg
// cada saco sólo puede llevar un regalo

carryGifts(['toy', 'gamme', 'toy', 'bike'], 6)
// ['toy', 'gamme', 'toy', 'bike']
// en cada saco se puede llevar 6kg
// cada saco sólo puede llevar un regalo
// fíjate que no se puede llevar 'toy toy' en un saco
// porque no está uno al lado del otro
```

<h3>Ten en cuenta:</h3>

<ul>
  <li>Los regalos siempre se agrupan por orden de aparición en el array.</li>
  <li>No puedes cambiar el orden de los regalos en el array a la hora de agruparlos.</li>
  <li>Se pueden agrupar todos los regalos en un solo saco.</li>
  <li>Si no se puede agrupar ningún regalo en un saco, se devuelve un array vacío.</li>
</ul>

<h2>Solucion</h2>

```js
function carryGifts(gifts, maxWeight) {
  return gifts.filter(g => g.length <= maxWeight)
    .reduce((acc, gift) => {
      const bag = acc.at(-1)
      const weight = bag.join('').length
      const fit = weight+gift.length<=maxWeight
      fit ? acc.at(-1).push(gift) : acc.push([gift])
      return acc
    }, [[]])
    .map(bag => bag.join(' '))
    .filter(bag => bag!='')
}
```
