# Instrucciones
<p>
Papá Noel se ha dado cuenta de que ni con la colaboración de todos los elfos va a poder entregar todos los regalos a tiempo. Por eso va a pedir ayuda a sus amigos de Autentia.

Desde Autentia nos han indicado que necesitan un programa para saber qué equipo de renos enviar a cada país. Hay diferentes tipos de renos y cada uno de ellos puede llevar un peso de regalos. Por ejemplo:
</p>

```js
const reindeerTypes = [
  { type: 'Nuclear', weightCapacity: 50 },
  { type: 'Electric', weightCapacity: 10 },
  { type: 'Gasoline', weightCapacity: 5 },
  { type: 'Diesel', weightCapacity: 1 }
]
```

<p>
En el listado de regalos que tiene Papá Noel se expresa cuánto pesa cada regalo y cuál es su país destino. El peso de los regalos siempre es un número natural. Por ejemplo:
</p>

```js
const gifts = [
  { country: 'Spain', weight: 30 },
  { country: 'Spain', weight: 7 },
  { country: 'France', weight: 17 }
]
```

<p>
Autentia nos comenta que, para que el equipo de renos a enviar a cada país sea óptimo, deberíamos:
</p>
<ul>
  <li>Enviar el mayor número de renos posibles de mayor capacidad de carga</li>
  <li>Aprovechar al máximo el peso que cada reno puede soportar.</li>
<li>Los renos tienen un comportamiento extraño y no admiten que en el equipo haya más renos de un tipo que renos del siguiente tipo por orden descendente de capacidad de carga.</li>
</ul>
<p>
Por ejemplo. A Francia (17) no se mandarían diecisiete renos diésel (17 * 1). Hay renos con mayor capacidad de carga, pero tampoco se mandaría un reno nuclear (50), ya que se estaría desaprovechando su capacidad. Se mandaría un reno eléctrico (10), uno gasolina (5) y dos diésel (2 * 1).
A España (37) no se podría mandar un equipo formado por tres eléctricos (3 * 10), uno gasolina (5) y dos diésel (2 * 1), ya que no puede haber más eléctricos que a gasolina. Tampoco dos eléctricos (2 * 10), tres gasolina (3 * 5) y dos diésel (2 * 1), pues no puede haber más a gasolina que a diésel. Habría que mandar dos eléctricos (2 * 10), dos a gasolina (2 * 5) y siete a diésel (7 * 1).
</p>

```js
const reindeerTypes = [
  { type: 'Nuclear', weightCapacity: 50 },
  { type: 'Electric', weightCapacity: 10 },
  { type: 'Gasoline', weightCapacity: 5 },
  { type: 'Diesel', weightCapacity: 1 }
]

const gifts = [
  { country: 'Spain', weight: 30 },
  { country: 'France', weight: 17 },
  { country: 'Italy', weight: 50 }
]

howManyReindeers(reindeerTypes, gifts)
// [{
//   country: 'Spain',
//   reindeers: [
//     { type: 'Electric', num: 1 },
//     { type: 'Gasoline', num: 3 },
//     { type: 'Diesel', num: 5 }
//   ]
// }, {
//   country: 'France',
//   reindeers: [
//     { type: 'Electric', num: 1 },
//     { type: 'Gasoline', num: 1 },
//     { type: 'Diesel', num: 2 }
//   ]
//  }, {
//   country: 'Italy',
//   reindeers: [
//     { type: 'Electric', num: 3 },
//     { type: 'Gasoline', num: 3 },
//     { type: 'Diesel', num: 5 }
//   ]
// }]
```

<h3>A tener en cuenta:</h3>
<ul>
  <li>Siempre habrá un tipo de reno con capacidad de carga 1.</li>
  <li>Siempre habrá al menos dos tipos de renos disponibles.</li>
  <li>No existe límite de renos de un mismo tipo a enviar siempre y cuando se ciña a las restricciones anteriormente expuestas.</li>
  <li>Los renos siempre estarán ordenados por capacidad de carga de mayor a menor.</li>
</ul>

<h1>Solucion</h1>

```js
function howManyReindeers(reindeerTypes, gifts) {
  reindeerTypes.sort((a, b) => b.weightCapacity - a.weightCapacity)
  return gifts.map(gift => {
    let totalSum = reindeerTypes.reduce((sum, r) => sum + r.weightCapacity, 0)
    const reindeers = reindeerTypes.map(r => {
      const num = Math.floor(gift.weight / totalSum)
      gift.weight -= num * r.weightCapacity
      totalSum -= r.weightCapacity
      return { type: r.type, num }
    }).filter(r => r.num)
    return { country: gift.country, reindeers }
  })
}
```
