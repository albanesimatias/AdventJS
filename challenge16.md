# Instrucciones

<p>
Papá Noel está empezando a recibir un montón de cartas pero tienen un montón de problemas de formato. Para mejorar la lectura, va a escribir un programa que, dado un texto, lo formatea de acuerdo a las siguientes reglas:
</p>
<ul>
<li>Eliminar espacios al inicio y al final</li>
<li>Eliminar múltiples espacios en blanco y dejar sólo uno</li>
<li>Dejar un espacio después de cada coma</li>
<li>Quitar espacios antes de coma o punto</li>
<li>Las preguntas sólo deben terminar con un signo de interrogación</li>
<li>La primera letra de cada oración debe estar en mayúscula</li>
<li>Poner en mayúscula la palabra "Santa Claus" si aparece en la carta</li>
<li>Poner un punto al final de la frase si no tiene puntuación</li>
<li>Las cartas las escriben inglés y aquí tenemos un ejemplo:</li>
</ul>

```js
fixLetter(` hello,  how are you??     do you know if santa claus exists?  i really hope he does!  bye  `)
// Hello, how are you? Do you know if Santa Claus exists? I really hope he does! Bye.

fixLetter("  Hi Santa claus. I'm a girl from Barcelona , Spain . please, send me a bike.  Is it possible?")
// Hi Santa Claus. I'm a girl from Barcelona, Spain. Please, send me a bike. Is it possible?
```

<h3>A tener en cuenta:</h3>

<ul>
  <li>No te tienes que preocupar por los signos de puntuación que no sean coma, punto o interrogación.</li>
  <li>Asegúrate de respetar los saltos de línea y espacios originales.</li>
</ul>

<a href="https://www.w3schools.com/jsref/jsref_obj_regexp.asp">Todo sobre REGEX</a>

<h2>Solución</h2>

```js
function fixLetter(letter) {
  return letter.trim()
    .replace(/,+/g, (x)=>', ')
    .replace(/\s+/g,' ')
    .replace(/([\.\?!]\s+)(.)|^./g, (c) => c.toUpperCase())
    .replace(/santa claus/gi, 'Santa Claus')
    .replace(/\s*\?+/g,'?')
    .replace(/\s+\./g, '.')
    .replace(/\s+,/g, ',')
    .replace(/\w$/, (l) => `${l}.`)
}
```
