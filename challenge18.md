# Instrucciones

<p>
Estamos imprimiendo los códigos de barra para los envíso. En la fábrica de Papá Noel usando un sistema de estampación de números donde cada número se imprime con una tinta diferente. Es un sistema antiguo pero fiable. Sin embargo, a veces nos quedamos sin tinta de un número.

Escribe una función que recibe el número del que no tenemos tinta (un número que será del 0 al 9) y como segundo parámetro, el número de códigos de barras que hay que imprimir (empezamos desde 1 hasta este número que recibimos).

Nos debe devolver un array con los números que incluyen el número que no tenemos tinta. Veamos un ejemplo:
</p>

```js
dryNumber(1, 15) // [1, 10, 11, 12, 13, 14, 15]

// no tenemos tinta para el 1
// tenemos que imprimir 15 códigos de barras del 1 al 15
// los códigos de barras que saldrán mal por falta de tinta son:
// 1, 10, 11, 12, 13, 14, 15

dryNumber(2, 20) // [2, 12, 20]

// no tenemos tinta para el 2
// tenemos que imprimir 20 códigos de barras del 1 al 20
// los códigos de barras que saldrán mal por falta de tinta son:
// 2, 12, 20
```

<h3>Ten en cuenta que:</h3>
<ul>
<li>El número del que no tenemos tinta sólo puede ser del 0 al 9.</li>
<li>El número del que no tenemos tinta puede estar en cualquier posición del código de barras.</li>
<li>El número de códigos de barras que hay que imprimir puede ser muy grande.</li>
</ul>

<h2>Solucion</h2>

```js
function dryNumber(dry, numbers) {
  return Array(numbers).fill().map((_,i)=>i+1)
            .filter(x=>`${x}`.includes(dry))
}
```
