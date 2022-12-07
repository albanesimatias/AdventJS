<h1>Instrucciones</h1>
<p>
Una pareja de entusiastas de la navidad ha creado una empresa de adornos navideños. El primer adorno que quieren fabricar es un cubo que se pone en los árboles.

El problema es que tienen que programar la máquina y no saben cómo hacerlo. Nos han pedido ayuda para lograrlo.

Para crear los cubos se le pasa un número con el tamaño deseado al programa y este devuelve un string con el diseño de ese tamaño. Por ejemplo, si le pasamos un 3, el programa debe devolver un cubo de 3x3x3:
</p>

```js
const cube = createCube(3)

  /\_\_\_\
 /\/\_\_\_\
/\/\/\_\_\_\
\/\/\/_/_/_/
 \/\/_/_/_/
  \/_/_/_/
```
<p>
Como ves el cubo tiene tres caras visualmente. Los símbolos que se usan para construir las caras del cubo son: /, \, _ y (espacio en blanco).

Otros ejemplos de cubos:
```js
const cubeOfOne = createCube(1)
  
/\_\
\/_/
```
Cosas a tener en cuenta:
<ul>
  <li>Fíjate bien en los espacios en blanco que hay en el cubo.</li>
  <li>El cubo tiene que ser simétrico.</li>
  <li>Asegúrate de usar los símbolos correctos.</li>
  <li>Cada nueva línea del cubo debe terminar con un salto de línea (\n) excepto la última.</li>
</ul>
</p>

<h2>Solucion</h2>

```js
function createCube(size) {
  let top = ''
  let bottom = ''
  for(let i=1,j=size; i<=size; i++, j--){
    top+=' '.repeat(size-i)+'/\\'.repeat(i)+'_\\'.repeat(size)+'\n'
    bottom+=' '.repeat(size-j)+'\\/'.repeat(j)+'_/'.repeat(size)+'\n'
  } 
  return top + bottom.slice(0,bottom.length-1)
}
```
