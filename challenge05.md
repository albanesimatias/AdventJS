<h1>Instrucciones</h1>
<p>
Para no cansar a los renos, Papá Noel quiere dejar el máximo número de regalos haciendo el menor número posible de viajes.

Tiene un array de ciudades donde cada elemento es el número de regalos que puede dejar allí. [12, 3, 11, 5, 7]. Por otro lado, el límite de regalos que caben en su saco. Y, finalmente, el número de ciudades máximo que sus renos pueden visitar.

Como no quiere dejar una ciudad a medias, si no puede dejar todos los regalos que son de esa ciudad, no deja ninguno allí.

Crea un programa que le diga la suma más alta de regalos que podría repartir teniendo en cuenta el máximo de regalos que puede transportar y el número máximo de ciudades que puede visitar:
</p>

```js
const giftsCities = [12, 3, 11, 5, 7]
const maxGifts = 20
const maxCities = 3

// la suma más alta de regalos a repartir
// visitando un máximo de 3 ciudades
// es de 20: [12, 3, 5]

// la suma más alta sería [12, 7, 11]
// pero excede el límite de 20 regalos y tendría
// que dejar alguna ciudad a medias.

getMaxGifts(giftsCities, maxGifts, maxCities) // 20
```
<p>
Si no se puede realizar ningún viaje que satisface los requerimientos, el resultado debe ser 0.
</p>

<p>
Cosas a tener en cuenta:
<ul>
  <li>maxGifts >= 1</li>
  <li>giftsCities.length >= 1</li>
  <li>maxCities >= 1</li>
  <li>El número de maxCities puede ser mayor a giftsCities.length</li>
</ul>
</p>

<h2>Solucion</h2>

```js
function getMaxGifts(giftsCities, maxGifts, maxCities) {
  return (() =>
    Math.max(
      ...giftsCities
        .reduce((a, c) => [...a, ...a.map((e) => [...e, ...[c]])], [[]])
        .filter((e) => e.length <= maxCities)
        .map((arr) => arr.reduce((a, c) => a + c, 0))
        .filter((n) => n <= maxGifts)
    ))()
}
```
