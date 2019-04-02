# console commands
@sergio 2

-  `pwd` muestra la ruta en la que nos encontramos

-  `/` indica la carpeta raíz

-  `.` indica la ubicación actual donde nos encontramos

-  `cd user/` entrar en directorio user

-  `rm -rf git-demo/` remove/borrar el directorio y su contenido (-r significa de manera recursiva) la 'f' significa force. no debemos poner una barra inicial que entonces empezaría a buscar la carpeta "git-demo" desde el directorio raíz (/)

-  `mkdir folder-name` crear carpeta con el nombre folder-name

-  `drwxr-xr-x 2 nico staff 68 7 ene 12:00 lab` drwxr-xr-x indica los permisos, nico indica el usuario que ha creado el archivo y staff el grupo al que pertenece este usuario

-  `cp file1 file2` copiar file1 a file2

-  `cp -r file2/ folder3` copiar la carpeta file2 y su contenido (gracias al flag r: -r) a la carpeta folder3

-  `mv file2 /file2` mover file2 a la carpeta /file2. Mover lo elimina desde el origen

-  `mv folder3/file2 folder3/file3` cambiar el nombre de file2 a file3, ambos archivos están dentro de la carpeta folder3

-  `tree` permite ver en forma de árbol la estructura de ficheros y carpetas. Hay que instalarlo

-  `man <command-name>` ver información de cualquier comando

-  `Cmd + k` limpiar pantalla

-  `Ctrl + l` limpiar pantalla

-  `chmod 664 file3` cambiar permisos del achivo file3

-  `echo "ciao mondo" > file4` echo se utiliza para enviar algo a consola y el símbolo > es enviar el contenido a un fichero

-  `history` ver el historial de comandos que has realizado

-  `find . -name file2` buscar un fichero o carpeta

-  `mkdir -p /folder1/folder2/folder3` crear varios directorios al mismo tiempo con la misma instrucción. Si folder1, folder2 y folder3 no existen se pueden crear al mismo tiempo

### `grep` command. One of the most useful commands on Linux

-  `grep -r . -e github` busca en el directorio actual (.) y sus subdirectorios (-r) cualquier archivo que contenga la palabra "github"

-  `grep 'word' filename` search any line that contains the word in filename on Linux

-  `grep -i 'bar' file1` a case-insensitive search for the word ‘bar’ in Linux and Unix

-  `grep -R 'foo'` search all files in the current directory and in all of its subdirectories in Linux for the word ‘foo’

-  `grep -c 'nixcraft' frontpage.md` search and display the total number of times that the string ‘nixcraft’ appears in a file named frontpage.md

-  `grep -r "192.168.1.5" /etc/` search recursively i.e. read all files under each directory for a string “192.168.1.5”

- `git stash` meter cajón temporal. 
- `git stash pop` sacar del cajón temporal.

  
### Otros 

-  **sass**: `sass --watch style.sass:style.css` enlazar archivo style.scss a style.css. Por ejemplo, si queremos hacer una escucha de un directorio entero de sass y volcarlo todo hacia un archivo en la ruta `static/css` el comando que debemos utilizar, situados en la raíz del proyecto: `sass --watch assets/sass/:static/css`
- **nano**: `ctrl + x` salir
- **nano**: `ctrl + o` guardar + ENTER


# Permisos - chmod

  
- grupo 1 - rwx - usuario que ha creado

- grupo 2 - r-x - grupo

- grupo 3 - r-x - otros grupos

  
**Ejemplo**: Cambiar a que el grupo puede escribir el archivo file3

-  `-rw-r--r-- 1 nico staff 25 7 ene 12:18 file3`

Si ejecutamos `chmod 664 file3`:

-  `rw-rw-r-- 1 nico staff 25 7 ene 12:18 file3`


# GIT

-  `git commit -m "initial import"` "initial import" típico 1er mensaje para el primer commit

-  `git show <id del log>` para ver los cambios que se han guardado en un ID en específico

-  `git checkout index.html` recuperar archivo index.html por ejemplo por si se ha borrado

-  `git diff` ver los cambios en específico

-  `git reset --hard HEAD` recupera el último commit de la rama donde estoy trabajando. Otra forma de hacerlo con un fichero concreto `git rm --cached index.html`

-  `git reset bbc23360b52fe7dd2a7c02c0cbcae7fa8d22c215` resetar/borrar todo el historial hasta el commit con ese ID

-  `git branch develop` crear rama nueva llamada develop

-  `git remote add origin https://github.com/nicopixel/git-demo.git` "origin" es la rama remota por defecto

-  `HEAD` significa el último commit

-  `git log --graph` ver detalles de la rama actual

-  `git log --graph --all` ver detalles de todas las ramas

- merge hace un auto commit internamente

-  `git push -u origin master` subir rama master al remoto por defecto (origin)

-  `git push -u origin develop` subir rama develop al remoto por defecto (origin)

-  `git push --set-upstream origin develop` se hace una única vez para cada rama. Es para tener las ramas sincronizadas entre remoto y local. También podemos indicar el nombre de la rama en remoto, en nuestro caso en develop

-  `git pull` integrar el estado actual DESDE remote en local. Por ejemplo, si tenemos cambios que queremos subir pero que pueden sobrescribir el código en remoto debemos hacer primero un GIT pull

-  `git branch -D feature/background-pink` borrar rama llamada feature/background-pink

-  `git checkout -b feature/cian` crear rama y cambiarse a ella

-  `git push origin --delete feature/body-border` borrar la rama feature/body-border de REMOTO

-  `git add .` esto sube todos los archivos en el directorio actual pero no es buena idea hacerlo. Lo recomendado es subir los archivos uno a uno

-  `git clone https://github.com/nicopixel/skylab-bootcamp-201901` clonar repositorio. Cuidado porque se clonan todas las ramas del repo de remoto. **Cuando hacemos un `git branch` en local NO vemos todas las ramas pero igualmente se puede cambiar a la rama aunque no la veamos**

-  `git config --list` mostrar la configuración de GIT

-  `git remote add upstream https://github.com/manuelbarzi/skylab-bootcamp-201901.git` Añadir otro repo remoto

-  `git branch -a` mostrar ramas ocultas

- Crear una copia **en local** de cualquier pull request para hacer pruebas en local debemos realizar los comandos que aparecen aquí: [Checking out pull requests locally](https://help.github.com/articles/checking-out-pull-requests-locally/)

-  `.gitignore` es un fichero que permite bloquear que se suban/commiteen los archivos específicos que se indican en ese fichero

-  `git add index.html;git commit -m "initial import"` se pueden separar varios comandos por `;`

-  `git fetch upstream` bajar los cambios del upstream a local

-  `git merge upstream/develop` mergear la rama bajada con develop

- `git clean -f -d` discard untracked files from the actual branch

-  **La rama MASTER no se toca**

-  **Tagear versiones**: Antes de entregar al cliente hay que tagear `git tag v1.0.0` y subir a remoto los tags por medio de `git push --tags` en este caso no se generan commits en remoto, se generan únicamente los tags.

-  `git tag v1.0.0` crear tags

-  `git push --tags` subir únicamente los tags

Los tags se utilizan para indicar las versiones:

<img  src="https://nhsconnect.github.io/gpconnect/images/design/semantic-versioning.png"  width="400px"  />

Los números de las versiones se indican con la sintaxis de `1.2.3`

-  `1` - indica cambios mayores que implican comportamiento profundo de la aplicación - Major

-  `2` - cambios menores - Minor

-  `3` - cambios ligeros - Patch

No hay una regla definida para definir qué cambio pertenece a cada categoría, más bien es **sentido común**

 ### Git merge open VIM editor (solution)
 
- Pulsar ESCAPE
- escribir `:w` para guardar o simplemente `:wq` para guardar y salir


### Pull Request (PR)  

Pull request es un método para comparar, comentar y trabajar en el código antes de hacer un merge. Se puede comentar en github de manera global y en cada línea.

Una vez aprobada la rama del compañero podemos hacer el Merge Pull Request.

Los pasos que llevaremos a cabo para trabajar con un proyecto donde **NO** somos colaboradores son los siguientes:

1. Forkeamos el proyecto original (Forkear es hacer una copia de un repo dentro de mi propio espacio de Github. Una vez 'forkeado' se trabaja en los cambios del código. ) => En github

2. Hacer un clone de mi repositorio forkeado => `git clone <url-del-proyecto>`

3. Se hacen los trabajos en local creando una rama => `git branch feature/branch-name` (también en este paso lógicamente hacemos un add y un commit)

4. Hacemos push a mi repositorio forkeado pero de la rama que hemos creado. Como esta rama es nueva y queremos subirla a REMOTO y que además esté sincronizada con mi repositorio en local recordar hacer la 1ª vez => `git push --set-upstream origin feature/branch-name` en caso de que la rama exista en remoto tan sólo bastaría con un `git push`

5. Aplicamos Pull-request de la rama nueva subida (`feature/branch-name`) hacia la rama develop => en github.

6. Por último, debemos hacer un Pull-request desde la rama develop de mi repo forkeado hacia el proyecto original que llamaremos upstream

No olvidar que tenemos que subir la rama de feature/nombre-rama a remoto. No vale con hacer git push, la primera vez que subimos la rama a remoto, tenemos que hacer un `git push --set-upstream origin feature/body-border`

- Siempre crear las ramas desde develop y no de una rama feature


### Git Flow  

-  **Rama master**: cualquier commit que pongamos en esta rama debe estar preparado para subir a producción

-  **Rama develop**: rama en la que está el código que conformará la siguiente versión planificada del proyecto

Cada vez que se incorpora código a master, tenemos una nueva versión. Además de estas dos ramas, Se proponen las siguientes ramas auxiliares:

-  **Feature**: Estas ramas se utilizan para desarrollar nuevas características de la aplicación que, una vez terminadas, se incorporan a la rama develop. Se originan y se incorporan siempre a la/desde rama develop.

-  **Release**: En estas ramas se hacen los últimos ajustes y se corrigen los últimos bugs antes de pasar el código a producción incorporándolo a la rama master. Se originan desde la rama develop pero se integran tanto en master como en develop.

-  **Hotfix**: Esas ramas se utilizan para corregir errores y bugs en el código en producción. Funcionan de forma parecida a las Releases Branches, siendo la principal diferencia que los hotfixes no se planifican. Se originan desde la rama Master y se integran tanto en master como en develop.


![Gitflow](https://datasift.github.io/gitflow/GitFlowHotfixBranch.png)

  

# HTML5 & CSS3

**HTML5** tiene semántica más descriptiva para que un spider pueda leer los elementos más importantes de la página.

-  [Listado de Tags de HTML5](https://www.tutorialrepublic.com/html-reference/html5-tags.php)

-  [Listado de selectores de CSS3](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)

-  [Pseudoclases & pseudoelements](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements)

Para ver si una etiqueta en específico es soportada por el navegador podemos usar la Web de [caniuse.com](https://caniuse.com/)

- Los `margin` se solapan y no se suman entre elementos

- El `border` crece hacia dentro

- Cuando usamos `box-sizing` el width y el height se tiene en cuenta desde el border del elemento

- Cuando usamos `display: inline` no se tiene en cuenta el width de elemento

- Cuando usamos `display: inline-block` si que podemos usar el width

- La idea de usar `float` viene para poner una imagen con un texto envolviendo la imagen

- Una imagen se comporta como un inline (aunque debería comportarse como inline-block). Aunque sea inline se le puede poner un width y un height.

- Cuando aplicamos un `float` se posiciona con respecto al elemento que le procede (elemento siguiente)

- La clase `position: sticky` sirve para dejar un elemento fijo con respecto al scroll de la página

- También se pueden utilizar unidades `em` y `rem`

- @imports siempre van al principio del archivo CSS

- Recordar siempre que al usar `inline-block` hay que eliminar los espacios y las nuevas líneas del código porque si no los elementos se mostrarán uno debajo de otro


# Visual Studio Code

-  `alt + SHIFT + f` tabular un código automáticamente

-  `cmd SHIFT + p` abrir buscador dentro del visual studio

-  `cmd + x` eliminar línea

-  `cmd + SHIFT + 7` comentar múltiples líneas

-  `alt + <flechas de movimiento>` mover líneas o bloques de texto hacia arriba o hacia abajo

- `cmd + click` nos lleva a la declaración de la función y con `ctrl -` nos lleva al punto anterior (llamada de la función)

- `fn + click` 

 
## Specificity CSS

  
**Specificity hierarchy**

1. Inline styles `<h1 style=“color: #fff;”>`

2.  \# of ID selectors `#div`

3. Classes (`.classes`), attributes (`[attributes]`) and pseudo-classes (`:hover`, `:focus`, `:invalid`)

4. Elements and pseudo-elements (`::before`)


# flex
```css

/*******container*********/
display: flex | inline-flex;
justify-content: [flex-start] | flex-end | center | space-between;
align-items: [flex-start] | flex-end | center; 
flex-direction: [row] | row-reverse | column | column-reverse; 
flex-wrap: nowrap | wrap | wrapreverse;
flex-flow: <flex-direction> <flex-wrap>;
align-content: flex-start | flex-end | center;

/*******elements*********/

order: <integer>;
align-self: flex-start | flex-end | center;
flex-basis: <length>; 
flex-grow: <number>;
flex-shrink: <integer>;
flex: <integer>; 

```

# Grid


```css

grid-column-start:


```


# SASS

### SASS - Media queries

- media queries in sass in `_mixins.sass` (usando mixins):

```sass
// Medium devices
@mixin md
	@media (min-width: #{$screen-md-min})
		@content

// Large devices
@mixin lg
	@media (min-width: #{$screen-lg-min})
		@content

// Extra large devices
@mixin xl
	@media (min-width: #{$screen-xl-min})
		@content
```

Cuando queremos usar esta media query debemos hacer:

```sass
#header
	padding: 1rem
	@include flex(flex,  space-between,  center)
	@include lg
		justify-content: flex-start
	&  .header__burger
		@include text(24,  28,  $color: #888888,  $family: "Font Awesome 5 Free",  $weight: 600)
		border: 1px  solid  #dddddd
		padding: 0.5rem  1rem
		border-radius: 0.4rem
		@include lg
			display: none
```

- La variable **lg** la tenemos definida en `_variables.sass` :

```sass
// MEDIA QUERIES
$screen-md-min: 580px
$screen-lg-min: 900px
$screen-xl-min: 1400px
```

### SASS - funciones - devuelven un valor
Ejemplo:

```sass
@function em($px,  $base: $base__font-size)
	@return ($px  /  $base) *  1em
```
Función para convertir pixeles a em. Ver uso abajo en mixins


### SASS - mixins

```sass
=text($size,  $line,  $weight: $base__weight, $family: $text__family-sans,  $color: $text__color--base)
	font-size: +em($size)
	line-height: ($line/$size)
	font-family: $family
	color: $color
	margin-bottom: +em($margin,  $size)
	font-weight: $weight
```

```sass
=flex($display: flex,  $justify-content: flex-start,  $align-items: flex-start,  $flex-flow: row  nowrap,  $align-content: flex-start)
	display: $display
	justify-content: $justify-content
	align-items: $align-items
	flex-flow: $flex-flow
	align-content: $align-content
```


 
# BEM

![](https://cdn-images-1.medium.com/max/1600/1*tBFD64u6_kmPVFNxjau17A.png)
  
```html
<!-- HEADER -->
<header id="header">
	<h3 class="header__logo">Gamma</h3>
	<i class="header__burger fas fa-bars"></i>
	<nav class="header__nav">
		<ul class="header__nav__menu">
			<li class="header__nav__menu__item">
				<a class="header__nav__menu__item__link" href="#">Home</a>
			</li>
			<li class="header__nav__menu__item">
				<a class="header__nav__menu__item__link" href="#">About</a>
			</li>
			<li class="header__nav__menu__item">
				<a class="header__nav__menu__item__link" href="#">Contact</a>
			</li>
		</ul>
	</nav>
</header>
```


### Diferencias entre responsive design y adaptive web design

-  **Responsive designs** respond to changes in browser width by adjusting the placement of design elements to fit in the available space.

-  **Adaptive Web Design** where responsive design relies on changing the design pattern to fit the real estate available to it, adaptive design has multiple fixed layout sizes. This kind of design use media-queries and breaking points



# JS
##BOM


![](https://boostlog-public.s3.us-west-1.amazonaws.com/articles/5ad587cb47018500491f3c36/html-dom-1523943362830.jpg)

Los eventos de javascript se pueden trabajar en **event capturing** (el evento se propaga de padre a hijo) y en **event bubbling** (el evento se propaga de hijo a padre). Por defecto, se trabaja en bubbling.

https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Examples#Example_5:_Event_Propagation

### variables

Cuando declaramos una variable vale undefined, también podemos asignarle null que sería que apunte a la 'nada' o lógicamente cuando tenga un valor


### Tipos de datos

- **primitivos**: numéricos, strings, undefined, null, boolean
- **no primitivos**: Objects, Arrays

Cuidado con esto. Los tipos de datos primitivos los pone en el mismo sitio en memoria

```js

/*Ejemplo 1*/
var o = { p: { n: 1 }}
var q = Object.assign({}, o)
o.p.n = 2
q.p.n // points to?

/*Ejemplo 2*/
var o = { p: { n: 1 }}
var q = {}
q.p = o.p
o.p.n = 3
q.p.n // ?

```

```js
 var o = {}
undefined
var p = {}
undefined
p == 0
false
p === o
false
p == o
false
```

Examples of _falsy_ values in JavaScript (which are coerced to false in Boolean contexts, and thus _bypass_ the `if` block):
```js
if (false)
if (null)
if (undefined)
if (0)
if (NaN)
if ('')
if ("")
if (``)
if (document.all)

```

```js
var a = 3
delete a // false

b = 3
delete b // true - se borra a

var o = {n:1}
delete o.n //{}
```

el typeof se usará bastante como en estos casos (el typeof se usa en primitivos)

```js
1 + '2' // lo convierte a string y devuelve 2
```

```js
var count = 10
for (; count--;) console.log(count) // imprime de 9 a 0
```

### instanceOf
Ver instanceOf, **se utiliza para objetos**

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
var auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// expected output: true

console.log(auto instanceof Object);
// expected output: true
```

### Use  `instanceof`  for custom types:

```js
var ClassFirst = function () {};
var ClassSecond = function () {};
var instance = new ClassFirst();
typeof instance; // object
typeof instance == 'ClassFirst'; // false
instance instanceof Object; // true
instance instanceof ClassFirst; // true
instance instanceof ClassSecond; // false 
```


### Also, use  `instanceof`  for complex built in types:

```js
/regularexpression/ instanceof RegExp; // true
typeof /regularexpression/; // object

[] instanceof Array; // true
typeof []; //object

{} instanceof Object; // true
typeof {}; // object
```

### Use  `typeof`  for simple built in types:

```js
'example string' instanceof String; // false
typeof 'example string' == 'string'; // true

'example string' instanceof Object; // false
typeof 'example string' == 'object'; // false

true instanceof Boolean; // false
typeof true == 'boolean'; // true

99.99 instanceof Number; // false
typeof 99.99 == 'number'; // true

function() {} instanceof Function; // true
typeof function() {} == 'function'; // true
```



El bucle `for ...in...` recorre tanto propiedades como métodos

```js
var obj = {a: 1, b: 2, c: 3};

for (const prop in obj) {
  console.log(`obj.${prop} = ${obj[prop]}`);
}

// Output:
// "obj.a = 1"
// "obj.b = 2"
// "obj.c = 3"
``` 


- Se debe realizar la documentación basada en http://usejsdoc.org/

# Error handling
## throw

The **`throw`  statement** throws a user-defined exception. Execution of the current function will stop (the statements after `throw` won't be executed), and control will be passed to the first [`catch`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) block in the call stack. If no `catch` block exists among caller functions, the program will terminate.

```js
function getRectArea(width, height) {
  if (isNaN(width) || isNaN(height)) {
    throw "Parameter is not a number!";
  }
}

try {
  getRectArea(3, 'A');
}
catch(e) {
  console.log(e);
  // expected output: "Parameter is not a number!"
}
```

You can specify an object when you throw an exception. You can then reference the object's properties in the `catch` block. The following example creates an object of type `UserException` and uses it in a `throw` statement.


```js
function UserException(message) {
   this.message = message;
   this.name = 'UserException';
}
function getMonthName(mo) {
   mo = mo - 1; // Adjust month number for array index (1 = Jan, 12 = Dec)
   var months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 
   'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
   if (months[mo] !== undefined) {
      return months[mo];
   } else {
      throw new UserException('InvalidMonthNo');
   }
}

try {
   // statements to try
   var myMonth = 15; // 15 is out of bound to raise the exception
   var monthName = getMonthName(myMonth);
} catch (e) {
   monthName = 'unknown';
   console.log(e.message, e.name); // pass exception object to err handler
}
```

You can use `throw` to rethrow an exception after you catch it. The following example catches an exception with a numeric value and rethrows it if the value is over 50. The rethrown exception propagates up to the enclosing function or to the top level so that the user sees it.

```js
try {
   throw n; // throws an exception with a numeric value
} catch (e) {
   if (e <= 50) {
      // statements to handle exceptions 1-50
   } else {
      // cannot handle this exception, so rethrow
      throw e;
   }
}
```


## try catch

The **`try...catch`** statement marks a block of statements to try, and specifies a response, should an exception be thrown.

```js
try {
  _try_statements_
}
[catch (_exception_var_1_ if _condition_1_) { // non-standard
  _catch_statements_1_
}]
...
[catch (_exception_var_2_) {
  _catch_statements_2_
}]
[finally {
  _finally_statements_
}]
```

The `try` statement consists of a `try` block, which contains one or more statements. `{}` must always be used, even for single statements.

At least one `catch` clause, or a `finally` clause, must be present. This gives us three forms for the `try` statement:

The `finally` clause executes after the `try` block and `catch` clause(s) execute but before the statements following the `try` statement. It always executes, regardless of whether an exception was thrown or caught.

**Hay que hacer un TypeError** cuando por ejemplo esperamos un objeto y nos envían un array. Se puede especificar que el error es de tipo TypeError.

### console.assert()
Writes an error message to the console if the assertion is false. If the assertion is true, nothing happens.

No depender de assert, es mejor utilizar un throw.

### compare 2 Arrays
array


### Closures

```js
var  times  =  function(n){
	return  function(x){
		return  x  *  n;
	}
}
var  times2  =  times(2);
console.log(times2(4));
```

ver ejemplos de Closures y practicar.


Otro ejemplo:

```js
function salute(name){
	return function(salutation){
		return salutation + ' ' + name + '!';
	}
}
var salute2 = salute('Sergio');
salute2('shut up'); //'shut up Sergio'
```

```js
function productMachine(products){
	return {
		
	}
}

var salute2 = salute('Sergio');
salute2('shut up'); //'shut up Sergio'

```

### IIFE

An **IIFE** (Immediately Invoked Function Expression) is a design pattern which is also known as a Self-Executing Anonymous Function

### call() & apply()
El call() y el apply() son dos métodos que se utilizan para llamar a funciones. Son métodos de funciones.

El call() se debe llamar con parámetros mientras que apply los argumentos se deben pasar en un array.

```js
function assign(name, surname){
	this.name = name;
	this.surname = surname;
}

var person = {};
assign.call(person, 'nico', 'martin');

assign.apply(person, ['nico', 'martin']);

person2 //{name: 'nico', surname: 'martin'}
```

El this es el contexto. 

# JavaScript Prototypes

## Effects of creating a function

1. A function is also an object and thus it can have additional properties.
2. A second object will be created and become attached to the function as  `<Function>.prototype`.

```js
function Person(name) {  
  this.name = name;  
}
typeof Person.prototype; // "object"
```

When we invoke the `Person` function with the `new` keyword, i.e. as a constructor, a new object `this` is implicitly created, `this.name` is set, and finally, `this` is implicitly returned.

```js
function Person(name) {  
  this.name = name;  
}

const alex = new Person("Alex");  
typeof alex; // "object"  
alex.name; // "Alex"
```

The object `alex` and any other object constructed from `Person`will gain indirect access to `Person.prototype`.

```js
Object.getPrototypeOf(alex) === Person.prototype; // true
```

If JavaScript cannot find the desired property on `alex`, it will check `Person.prototpe`. In other words, `alex`’s prototype chain starts with `Person.prototype`.

```js
 Object.getPrototypeOf(Person.prototype)  === Object.prototype; // true
```

#### Important

1.  `alex`  was constructed from  `Person`.  
    The prototype of  `alex`  is  `Person.prototype`.
2.  `Person.prototype`  was constructed from  `Object`.  
    The prototype of  `Person.prototype`  is  `Object.prototype`.

this es exactly equal to:

1.  `Person.prototype`  was constructed from  `Object`.  
    The prototype of  `Person.prototype`  is  `Object.prototype`.
2.  `Object.prototype`  was constructed from  `Object`.  

`alex`’s prototype chain contains `Person.prototype` followed by `Object.prototype`.


**End of the chain: => null**

```js
Object.getPrototypeOf(Object.prototype) === null; // true 
```

This property also applies to plain objects created from the built-in `Object` constructor and the object literal syntax.

```js
const constructedObject = new Object();  
const objectLiteral = {};
Object.getPrototypeOf(constructedObject) ===  Object.prototype; // true  
Object.getPrototypeOf(objectLiteral) === Object.prototype; // true
```

The fact that nearly all objects have `Object.prototype` at the end of their prototype chains is of practical significance because they will have access to common utilities offered by `Object.prototype` such as `toString` and `valueOf`.

## A function’s prototype

Remember the Person Function:

```js
function Person(name) {  
  this.name = name;  
}
```

We think that `alex.name` is not just any random name that happens to be accessible at `alex.name`, but instead refers to **Alex’s name**.  What about `Person.prototype`? Does it refer to `Person`**’s prototype**? 

**¡AND THE ANSWER IS NO!**

```js
Object.getPrototypeOf(Person) !== Person.prototype; // true
```
So what is the actual prototype of `Person`? It is `Function.prototype`. This is because `Person` is a `Function` and thus it has a prototype of `Function.prototype`.

```js
Object.getPrototypeOf(Person) === Function.prototype; // true
```

`Function.prototype` offers common utilities like `call`, `bind` and `apply`which can be accessed from `Person` and other functions.


### Prototypes without constructors

```js
const greeter = {  
  greet() {  
    console.log(`Hi ${this.name}`);  
  }  
};

const bob = Object.create(greeter);  
bob.name = "Bob";  
bob.greet(); // "Hi Bob"

Object.getPrototypeOf(bob) === greeter; // true
```

`Object.create` created a new object with `greeter` as its prototype.




### Métodos estáticos

Existen métodos que no están en el prototype sino que son propiedades de la clase ( por ejemplo, Array.from() ) Son métodos estáticos ya que no necesitan crear un objeto o una instancia para utilizarlos. 

No forman parte de la instancia sino del propio tipo o también se dice que son utilitarios del propio tipo. 

Cuando necesitemos operar de forma estática debemos crear un método como propiedad de clase.



# AJAX

```js
var form = document.getElementsByTagName('form')[0];
var input = document.getElementsByTagName('input')[0];
var list = document.getElementsByTagName('ul')[0];

form.addEventListener('submit', function (event) {
	event.preventDefault();
	var query = input.value;
	search(query);
});

function search(query) {
	var xhr = new XMLHttpRequest;
	xhr.open('GET', 'https://duckling-api.herokuapp.com/api/search?q=' + query);
	
	xhr.onload = function () {
		var res = JSON.parse(xhr.responseText);
		list.innerHTML = '';
		if (res.error)
			listNoResults(res.error);
		else
			listResults(res.data);
	};
	xhr.send();
}

function listNoResults(message) {
	var item = document.createElement('li');
	item.innerText = message;
	list.appendChild(item);
}

function listResults(ducklings) {
	ducklings.forEach(function (duckling) {
		var item = document.createElement('li');
		item.innerText = duckling.title;
		var image = document.createElement('img');
		image.src = duckling.imageUrl;
		image.style.width = '100px';
		item.appendChild(image);
		list.appendChild(item);
	});
}
```


# Recursive Functions

Utilizaremos una lamada a una función forEach en la que no podemos utilizar bucles de iteración:

```js
var  arr  = ['a', 'b', 'c', 'd', 'e'];
forEach(arr, console.log);
```

Entonces podemos definir la función forEach de muchas formas diferentes:

**Forma 1:**
```js
function  forEach(array, callback, count) {
	count  =  typeof  count  ===  'undefined'  ?  0  :  count;
	if (count  <  array.length) {
		callback(array[count++]);
		forEach(array, callback, count);
	}
}
```

**Forma 2: podemos meter el count en una propiedad de la función**
```js
function  forEach(array, callback) {
	forEach.count = typeof forEach.count === 'undefined'  
	? 0 : forEach.count;
	if (forEach.count  <  array.length) {
		callback(array[forEach.count++]);
		forEach(array, callback, forEach.count);
	} else  forEach.count  =  0;
}
```

**Forma 3: podemos meterlo en una IIFE (Immediately Invoked Function Expressions)**
```js
var  forEach  = (function() {
	var  count  =  0;
	return  function(array, callback) {
		if (count  <  array.length) {
			callback(array[count++]);
			forEach(array, callback);
		} else  count  =  0;
	}
})();
```
**Forma 4**
```js
var  forEach  =  initForEach();

function  initForEach() {
	var  count  =  0;
	return  function(array, callback) {
		if (count  <  array.length) {
			callback(array[count++]);
			forEach(array, callback);
		} else  count  =  0;
	}
}
```

**Forma 5 - la más limpia**

```js
function  forEach(array, callback) {
	if (array.length) {
		callback(array[0]);
		forEach(array.slice(1), callback);
	}
}
```

# Jasmine

```js
expect(isHorroy2).toBe(false);
expect(isHorroy2).toBeFalsy();
expect(horr.length).toBe(1);
expect(instance).toBe(instance);
expect(number).toBeCloseTo(number, decimalPlaces);
expect(mixed).toBeDefined();
expect(mixed).toBeFalsy();
expect(number).toBeGreaterThan(number);
expect(number).toBeLessThan(number);
expect(number).toBeNaN();
expect(mixed).toBeNull();
expect(mixed).toBeTruthy();
expect(mixed).toBeUndefined();
expect(array).toContain(member);
expect(mixed).toEqual(mixed);
expect(spy).toHaveBeenCalled();
expect(spy).toHaveBeenCalledTimes(number);
expect(spy).toHaveBeenCalledWith(...arguments);
expect(mixed).toMatch(pattern);
expect(fn).toThrow(string);
expect(fn).toThrowError(string);

```

# DOM Manipulation with vanilla JS
```js
var  loginPanel  =  new  LoginPanel
document.body.appendChild(loginPanel.element);
```

```js
function  LoginPanel() {
	Panel.call(this, document.createElement('section'));

	var  container  =  this.element;
	container.className  =  'login';

	var  title  =  document.createElement('h2');
	title.innerText  =  'Login';
	container.appendChild(title);

	var  form  =  document.createElement('form');
	form.className  =  'login__form';
	container.appendChild(form);
	this.__form__  =  form;

	var  emailLabel  =  document.createElement('label');
	emailLabel.setAttribute('for', 'email');
	emailLabel.innerText  =  'E-mail:';
	form.appendChild(emailLabel);

	var  emailInput  =  document.createElement('input');
	emailInput.type  =  'email';
	emailInput.name  =  'email';
	emailInput.placeholder  =  'email';
	emailInput.required  =  true;
	form.appendChild(emailInput);
	this.__emailInput__  =  emailInput;
```


# Bind

### Example 1 bind()
```js
Object.defineProperty(SearchPanel.prototype, 'onSearch', {
	set:  function (callback) {
			this.__$form__.on('submit', function (event) {
			event.preventDefault();
			var  query  =  this.__$queryInput__.val();
			callback(query);
		}.bind(this));
	}
});
```


### Example 2 bind()

```js
Object.defineProperty(SearchPanel.prototype, 'results', {
	set:  function (results) {
		this.__$resultList__.empty();
		this.__errorPanel__.hide();
		results.forEach(function (result) {
			var  $item  =  $('<li></li>');
			$item.append(result.text);
			var  $image  =  $('<img>');
			$image.attr('src', result.image).width(100);
			$item.append($image);
			this.__$resultList__.append($item);
		}.bind(this));
	}
});
```

# $(jQuery)

### Code snippet examples using jQuery

```js
var  searchPanel  =  new  SearchPanel
var  $body  =  $(document.body);
$body.append(loginPanel.$element);
```

```js
function  SearchPanel() {
Panel.call(this, $('<section>'
	+  '<form>'
	+  '<input type="text" name="query" placeholder="...">'
	+  '<button type="submit">Search</button>'
	+  '</form>'
	+  '<ul></ul>'
	+  '</section>'));
var  $container  =  this.$element;
var  $form  =  $container.children('form'); 
```

```js
Object.defineProperty(LoginPanel.prototype, 'onLogin', {
	set:  function (callback) {
		this.__$form__.on('submit', function (event) {
			event.preventDefault();
			var  email  =  this.__$emailInput__.val();
			var  password  =  this.__$passwordInput__.val();
			callback(email, password);
		}.bind(this));
	}
});
```

```js
RegisterPanel.prototype.clear  =  function () {
	this.__$nameInput__.val('');
	this.__$surnameInput__.val('');
	this.__$emailInput__.val('');
	this.__$passwordInput__.val('');
	this.__$passwordConfirmationInput__.val('');
	this.__errorPanel__.message  =  '';
	this.__errorPanel__.hide();
};
```

```js
function  HomePanel() {
	Panel.call(this, $('<section class="home">'
		+  '<h2>Welcome, <span></span>!</h2>'
		+  '<button>Logout</button>'
	));
	var  $container  =  this.$element;
	this.__$userSpan__  =  $container.children('h2').children('span');
	this.__$logoutButton__  =  $container.children('button');
}
```

```js
Object.defineProperty(SearchPanel.prototype, 'results', {
	set:  function (results) {
		this.__$resultList__.empty();
		this.__errorPanel__.hide();
		results.forEach(function (result) {
			var  $item  =  $('<li></li>');
			$item.append(result.text);
			var  $image  =  $('<img>');
			$image.attr('src', result.image).width(100);
			$item.append($image);
			this.__$resultList__.append($item);
		}.bind(this));
	}
});
```

```js
var  $inputs  =  $form.children('input');
this.__$nameInput__  =  $($inputs[0]);
this.__$surnameInput__  =  $($inputs[1]);
this.__$emailInput__  =  $($inputs[2]);
this.__$passwordInput__  =  $($inputs[3]);
this.__$passwordConfirmationInput__  =  $($inputs[4]);
```



### Doc

<table class="w3-table-all notranslate">
<tbody><tr>
<th style="width:23%">Mouse Events</th>
<th style="width:25%">Keyboard Events</th>
<th style="width:22%">Form Events</th>
<th>Document/Window Events</th>
</tr>
<tr>
<td>click</td>
<td>keypress</td>
<td>submit</td>
<td>load</td>
</tr>
<tr>
<td>dblclick</td>
<td>keydown</td>
<td>change</td>
<td>resize</td>
</tr>
<tr>
<td>mouseenter</td>
<td>keyup</td>
<td>focus</td>
<td>scroll</td>
</tr>
<tr>
<td>mouseleave</td>
<td>&nbsp;</td>
<td>blur</td>
<td>unload</td>
</tr>
</tbody></table>

### jQuery selectors

#### Basic Selectors
<table class="data">
							<tbody><tr>
								<th style="width: 100px;">Selector</th>
								<th style="width: 150px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>*</code></td>
								<td><code>$("*")</code></td>
								<td>Selects all elements.</td>
							</tr>
							<tr>
								<td><code><em>#id</em></code></td>
								<td><code>$("#foo")</code></td>
								<td>Selects all elements with the <code>id="foo"</code>.</td>
							</tr>
							<tr>
								<td><code><em>.class</em></code></td>
								<td><code>$(".bar")</code></td>
								<td>Selects all elements with the <code>class="bar"</code>.</td>
							</tr>
							<tr>
								<td><code><i>element</i></code></td>
								<td><code>$("p")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements.</td>
							</tr>
							<tr>
								<td><code><i>selector1, selector2, selectorN</i></code></td>
								<td><code>$("h1,&thinsp;p.bar,&thinsp;span")</code></td>
								<td>Selects all <code>&lt;h1&gt;</code> and <code>&lt;span&gt;</code>, but only that <code>&lt;p&gt;</code> elements that has the <code>class="bar"</code>.</td>
							</tr>
						</tbody></table>


#### Content Filter Selectors

<table class="data">
							<tbody><tr>
								<th style="width: 100px;">Selector</th>
								<th style="width: 150px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>:contains()</code></td>
								<td><code>$('p:contains("Hello")')</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements that contains the text "Hello".</td>
							</tr>
							<tr>
								<td><code>:empty</code></td>
								<td><code>$("td:empty")</code></td>
								<td>Selects all <code>&lt;td&gt;</code> elements that are empty i.e that have no children including text.</td>
							</tr>
							<tr>
								<td><code>:has()</code></td>
								<td><code>$("p:has(img)")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements which contain at least one <code>&lt;img&gt;</code> element.</td>
							</tr>
							<tr>
								<td><code>:parent</code></td>
								<td><code>$(":parent")</code></td>
								<td>Select all elements that have at least one child node either an element or text.</td>
							</tr>
						</tbody></table>

#### Form Selectors
<table class="data">
							<tbody><tr>
								<th style="width: 100px;">Selector</th>
								<th style="width: 150px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>:input</code></td>
								<td><code>$(":input")</code></td>
								<td>Selects all input, textarea, select and button elements (basically selects all form controls).</td>
							</tr>
							<tr>
								<td><code>:text</code></td>
								<td><code>$(":text")</code></td>
								<td>Selects all input elements with <code>type="text"</code>.</td>
							</tr>
							<tr>
								<td><code>:password</code></td>
								<td><code>$(":password")</code></td>
								<td>Selects all input elements with <code>type="password"</code>.</td>
							</tr>
							<tr>
								<td><code>:radio</code></td>
								<td><code>$(":radio")</code></td>
								<td>Selects all input elements with <code>type="radio"</code>.</td>
							</tr>
							<tr>
								<td><code>:checkbox</code></td>
								<td><code>$(":checkbox")</code></td>
								<td>Selects all input elements with <code>type="checkbox"</code>.</td>
							</tr>							
							<tr>
								<td><code>:button</code></td>
								<td><code>$(":button")</code></td>
								<td>Selects all input and button elements with <code>type="button"</code>.</td>
							</tr>
							<tr>
								<td><code>:submit</code></td>
								<td><code>$(":submit")</code></td>
								<td>Selects all input and button elements with <code>type="submit"</code>.</td>
							</tr>
							<tr>
								<td><code>:reset</code></td>
								<td><code>$(":reset")</code></td>
								<td>Selects all input and button elements with <code>type="reset"</code>.</td>
							</tr>
							<tr>
								<td><code>:image</code></td>
								<td><code>$(":image")</code></td>
								<td>Selects all input elements with <code>type="image"</code>.</td>
							</tr>
							<tr>
								<td><code>:file</code></td>
								<td><code>$(":file")</code></td>
								<td>Selects all input elements with <code>type="file"</code>.</td>
							</tr>
							<tr>
								<td><code>:enabled</code></td>
								<td><code>$(":enabled")</code></td>
								<td>Selects all elements that are enabled.</td>
							</tr>
							<tr>
								<td><code>:disabled</code></td>
								<td><code>$(":disabled")</code></td>
								<td>Selects all elements that are disabled.</td>
							</tr>
							<tr>
								<td><code>:selected</code></td>
								<td><code>$(":selected")</code></td>
								<td>Selects all elements that are selected, only works for <code>&lt;option&gt;</code> elements.</td>
							</tr>
							<tr>
								<td><code>:checked</code></td>
								<td><code>$(":checked")</code></td>
								<td>Selects all elements that are checked or selected, works for checkboxes, radio buttons, and select elements.</td>
							</tr>
							<tr>
								<td><code>:focus</code></td>
								<td><code>$(":focus")</code></td>
								<td>Selects element if it is currently focused.</td>
							</tr>
						</tbody></table>

####  Attribute Selectors

<table class="data">
							<tbody><tr>
								<th style="width: 155px;">Selector</th>
								<th style="width: 150px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>[attribute]</code></td>
								<td><code>$("[href]")</code></td>
								<td>Selects all elements with a <code>href</code> attribute, with any value.</td>
							</tr>
							<tr>
								<td><code>[attribute="value"]</code></td>
								<td><code>$('a[target="_blank"]')</code></td>
								<td>Selects all <code>&lt;a&gt;</code> elements that have the <code>target</code> attribute with a value equal to <code>"_blank"</code>.</td>
							</tr>
							<tr>
								<td><code>[attribute="value"]</code></td>
								<td><code>$('a[target!="_blank"]')</code></td>
								<td>Selects all <code>&lt;a&gt;</code> elements that don't have the <code>target</code> attribute, or if have don't with a value <code>"_blank"</code>.</td>
							</tr>
							<tr>
								<td><code>[attribute$="value"]</code></td>
								<td><code>$('img[src$=".png"]')</code></td>
								<td>Selects all <code>&lt;img&gt;</code> elements that have the <code>src</code> attribute with a value ending with <code>".png"</code>.</td>
							</tr>
							<tr>
								<td><code>[attribute|="value"]</code></td>
								<td><code>$('a[hreflang|="en"]')</code></td>
								<td>Selects all <code>&lt;a&gt;</code> elements that have the <code>hreflang</code> attribute with a value equal to <code>"en"</code>, or starting with <code>"en"</code> followed by a hyphen,&thinsp;like <code>"en-US"</code>.</td>
							</tr>
							<tr>
								<td><code>[attribute^="value"]</code></td>
								<td><code>$('img[title^="Smiley"]')</code></td>
								<td>Selects all <code>&lt;img&gt;</code> elements that have the <code>title</code> attribute with a value beginning exactly with a "Smiley" string.</td>
							</tr>
							<tr>
								<td><code>[attribute~="value"]</code></td>
								<td><code>$('img[title~="Kites"]')</code></td>
								<td>Selects all <code>&lt;img&gt;</code> elements that have the <code>title</code> attribute with a value containing the word "Kites", delimited by spaces.</td>
							</tr>
							<tr>
								<td><code>[attribute*="value"]</code></td>
								<td><code>$('input[name*="male"]')</code></td>
								<td>Selects all <code>&lt;input&gt;</code> elements that have the <code>name</code> attribute with&thinsp;a&thinsp;value containing the substring "male".</td>
							</tr>
						</tbody></table>

#### Hierarchy Selectors

<table class="data">
							<tbody><tr>
								<th style="width: 155px;">Selector</th>
								<th style="width: 115px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>parent &gt; child</code></td>
								<td><code>$("ul &gt; li")</code></td>
								<td>Selects all <code>&lt;li&gt;</code> elements that are direct child of their parent <code>&lt;ul&gt;</code> element.</td>
							</tr>
							<tr>
								<td><code>ancestor&nbsp;descendant</code></td>
								<td><code>$("form label")</code></td>
								<td>Selects all <code>&lt;label&gt;</code> elements that are descendant of their ancestor <code>&lt;form&gt;</code> element.</td>
							</tr>
							<tr>
								<td><code>prev + next</code></td>
								<td><code>$("h1 + p")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements that are next i.e. immediately preceded to the <code>&lt;h1&gt;</code> elements.</td>
							</tr>
							<tr>
								<td><code>prev ~ siblings</code></td>
								<td><code>$("h1 ~ p")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements that are siblings and follow after the <code>&lt;h1&gt;</code> elements.</td>
							</tr>
						</tbody></table>

#### Visibility Filter Selectors

<table class="data">
							<tbody><tr>
								<th style="width: 100px;">Selector</th>
								<th style="width: 150px;">Example</th>
								<th>Description</th>
							</tr>
							<tr>
								<td><code>:hidden</code></td>
								<td><code>$("p:hidden")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements that are hidden.</td>
							</tr>
							<tr>
								<td><code>:visible</code></td>
								<td><code>$("p:visible")</code></td>
								<td>Selects all <code>&lt;p&gt;</code> elements that are visible.</td>
							</tr>
						</tbody></table>


###  Traversing Siblings

-   `siblings()`
-   `next()`
-   `nextAll()`
-   `nextUntil()`
-   `prev()`
-   `prevAll()`
-   `prevUntil()`

### Traversing Down 

-   `children()`
-   `find()`

### Traversing Up

-   `parent()`
-   `parents()`
-   `parentsUntil()`

### Traversing -  Filtering

- `first()`
- `last()` 
- `eq()`

### Others
`filter()` and `not()` allow you to select elements that match, or do not match, a certain criteria.


