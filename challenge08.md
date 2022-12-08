# Instrucciones

<p>
Se han estropeado algunos trineos eléctricos y los elfos están buscando piezas de respuesto para arreglarlos, pero no tienen claro si las piezas que tienen sirven.

Las piezas de repuesto son cadenas de texto y el mecánico Elfon Masc ha dicho que una pieza de repuesto es válida si la pieza puede ser un palíndromo después de eliminar, como máximo, un carácter.

Un palíndromo es una palabra o frase que se lee igual de izquierda a derecha que de derecha a izquierda.

Nuestra función debe devolver un booleano que indique si la pieza de repuesto es válida o no con esa regla:
</p>

```js
checkPart("uwu") // true
// "uwu" es un palíndromo sin eliminar ningún carácter

checkPart("miidim") // true
// "miidim" puede ser un palíndromo después de eliminar la primera "i"
// ya que "midim" es un palíndromo

checkPart("midu") // false
// "midu" no puede ser un palíndromo después de eliminar un carácter
```
<h2>Solucion</h2>

```js
function checkPart(part) {
  let cont = 0
  for(let i=0, j=part.length-1; i<j; i++,j--){
    if(part.charAt(i) == part.charAt(j))
      continue
    cont++
    if(cont > 1) return false
    if(part.charAt(i+1) == part.charAt(j)) i++
    if(part.charAt(i) == part.charAt(j-1)) j--
  }
  return true
}
```
