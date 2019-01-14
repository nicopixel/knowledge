
<hr>

# console commands


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

  

## `grep` command. One of the most useful commands on Linux

-  `grep -r . -e github` busca en el directorio actual (.) y sus subdirectorios (-r) cualquier archivo que contenga la palabra "github"

-  `grep 'word' filename` search any line that contains the word in filename on Linux

-  `grep -i 'bar' file1` a case-insensitive search for the word ‘bar’ in Linux and Unix

-  `grep -R 'foo'` search all files in the current directory and in all of its subdirectories in Linux for the word ‘foo’

-  `grep -c 'nixcraft' frontpage.md` search and display the total number of times that the string ‘nixcraft’ appears in a file named frontpage.md

-  `grep -r "192.168.1.5" /etc/` search recursively i.e. read all files under each directory for a string “192.168.1.5”

  
### Otros 

-  **sass**: `sass --watch style.sass:style.css` enlazar archivo style.scss a style.css
- **nano**: `ctrl + x` salir

- **nano**: `ctrl + o` guardar + ENTER

___

# Permisos - chmod

  
- grupo 1 - rwx - usuario que ha creado

- grupo 2 - r-x - grupo

- grupo 3 - r-x - otros grupos

  
**Ejemplo**: Cambiar a que el grupo puede escribir el archivo file3

-  `-rw-r--r-- 1 nico staff 25 7 ene 12:18 file3`

Si ejecutamos `chmod 664 file3`:

-  `rw-rw-r-- 1 nico staff 25 7 ene 12:18 file3`

<hr>

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

-  `git merge upstream/develop` traer la rama develop de upstream a nuestra rama develop de local

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

  
## Pull Request (PR)  

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

  

<hr>

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

  
 
## Specificity CSS

  
Specificity hierarchy

1. Inline styles `<h1 style=“color: #fff;”>`

2.  \# of ID selectors `#div`

3. Classes (`.classes`), attributes (`[attributes]`) and pseudo-classes (`:hover`, `:focus`, `:invalid`)

4. Elements and pseudo-elements (`::before`)

<hr>

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

# smacss

- keep CSS more organized and more structured
- SMACSS (pronounced “smacks”) is more style guide than rigid framework

There are five types of categories:
1.  Base
2.  Layout
3.  Module
4.  State
5.  Theme

- Much of the purpose of categorizing things is to codify patterns

### Base rules
Are the defaults. They are almost exclusively single element selectors but it could include attribute selectors, pseudo-class selectors, child selectors or sibling selectors:

````css
/* Example of Base Rules */
html, body, form { margin: 0; padding: 0; } 
input[type=text] { border: 1px solid #999; } 
a { color: #039; } 
a:hover { color: #03C; }
````

I highly recommended that you specify a body background. Some users may define their own background as something other than white. If you work off the expectation that the background will be white, your design may look broken. Worse, your font colour choice may clash with the user’s setting and make your site unusable.

**A CSS Reset is a set of Base styles**

### Layout rules  

Divide the page into sections. **Layouts hold one or more modules together**

The minor components (**modules**)—such as a callout, or login form, or a navigation item—sit within the scope of major components  (go inside) such as a header or footer.

Layout styles can also be divided into major and minor styles based on reuse. Major layout styles such as header and footer are traditionally styled using ID selectors but **take the time to think about the elements that are common across all components of the page and use class selectors** where appropriate.

````css
#header, #article, #footer { width: 960px; margin: auto; }
#article { border: solid #CCC; border-width: 1px 0 0; }
````

There is minor Layout styles will use class names instead of IDs so that the styles can be used multiple times on the page.

Generally, a Layout style only has a single selector: a single ID or class name. However, there are times when a Layout needs to respond to different factors. For example, you may have different layouts based on user preference. This layout preference would still be declared as a Layout style and used in combination with other Layout styles.

````css
/* the .l-flipped class is applied on a higher level element such as the body element and allows the article and sidebar content to be swapped */
#article { float: left; } 
#sidebar { float: right; } 
.l-flipped #article { float: right; } 
.l-flipped #sidebar { float: left; }
````


Layout styles are the only primary category type to use ID selectors, **if you choose to use them at all**



CSS, by its very nature, is used to lay elements out on the page. However, there is a distinction between layouts dictating the major and minor components of a page. The minor components—such as a callout, or login form, or a navigation item—sit within the scope of major components such as a header or footer. I refer to the minor components as Modules and will dive into those in the next section. The major components are referred to as Layout styles.

Layout styles can also be divided into major and minor styles based on reuse. Major layout styles such as header and footer are traditionally styled using ID selectors but take the time to think about the elements that are common across all components of the page and use class selectors where appropriate.

Layout declarations

```
#header, #article, #footer {
    width: 960px;
    margin: auto;
}

#article {
    border: solid #CCC;
    border-width: 1px 0 0;
}

```

Some sites may have a need for a more generalized layout framework (for example,  [960.gs](http://960.gs/)). These minor Layout styles will use class names instead of IDs so that the styles can be used multiple times on the page.

Generally, a Layout style only has a single selector: a single ID or class name. However, there are times when a Layout needs to respond to different factors. For example, you may have different layouts based on user preference. This layout preference would still be declared as a Layout style and used in combination with other Layout styles.

Use of a higher level Layout style affecting other Layout styles.

```
#article {
    float: left;
}

#sidebar {
    float: right;
}

.l-flipped #article {
    float: right;
}

.l-flipped #sidebar {
    float: left;
}

```

In the Layout example, the .l-flipped class is applied on a higher level element such as the body element and allows the article and sidebar content to be swapped, moving the sidebar from the right to the left and vice versa for the article.

Using two Layout styles together to switch from fluid to fixed layout.

```
#article {
    width: 80%;
    float: left;
}

#sidebar {
    width: 20%;
    float: right;
}

.l-fixed #article {
    width: 600px;
}

.l-fixed #sidebar {
    width: 200px;
}

```



In this last example, the  `.l-fixed`  class modifies the design to change the layout from fluid (using percentages) to fixed (using pixels).

One other thing to note in the Layout example is the naming convention that I have used. The declarations that use ID selectors are named accurately and with no particular namespacing. The class-based selectors, however,  _do_  use an  `l-`  prefix. This helps easily identify the purpose of these styles and separate them from Modules or States. Layout styles are the only primary category type to use ID selectors, if you choose to use them at all. If you wish to namespace your ID selectors, you can, but it is not as necessary to do so.

#### Using ID selectors

To be clear, using ID attributes in your HTML can be a good thing and in some cases, absolutely necessary. For example, they provide efficient hooks for JavaScript. For CSS, however, ID selectors aren’t necessary as the performance difference between ID and class selectors is nearly non-existent and can make styling more complicated due to increasing specificity.

![](https://smacss.com/img/lyt-cnn1.png)

Another part of this website:

![](https://smacss.com/img/lyt-cnn-ft0.png)

```html
<div> 
	<h2>Featured</h2> 
	<ul> 
		<li><a href="…">…</a></li> <li><a href="…">…</a></li> 
		… 
	</ul> 
</div>
```
A possible approach to styling the list of featured items. (without considering the SMACSS)


```css
div#featured ul { 
	margin: 0; 
	padding: 0; 
	list-style-type: none; 
} 
div#featured li { 
	float: left; 
	height: 100px; 
	margin-left: 10px; 
}
```

Looking back at the code example, there are definitely some optimizations that could be made. The ID selector didn’t need to be qualified with a tag selector, too, and since the list is a direct descendant of the `div`, the child selector (>) could’ve been used.

From a layout perspective, all we care about is how each item relates to each other.

```css
.l-grid { 
	margin: 0; 
	padding: 0; 
	list-style-type: none; 
} 
.l-grid > li { 
	display: inline-block; 
	margin: 0 0 10px 10px; 
}
```

**Very rarely does _any_ solution solve 100% of the problem.**

### Modules Rules

**Modules**  are the reusable, modular parts of our design. They are the callouts, the sidebar sections, the product lists and so on. This is the meat of the page.  Each Module should be designed to exist as a standalone component. Modules can easily be moved to different parts of the layout without breaking. Modules can sometimes sit within other Modules.

Using `.module span` is great if a span will predictably be used and styled the same way every time while within that module.

```html
<div class="fld"> 
	<span>Folder Name</span> 
</div> 

/* The Folder Module */ 
.fld > span { 
	padding-left: 20px; 
	background: url(icon.png); 
}
```


What happen if we do this:

```html
	<div class="fld"> 
		<span>Folder Name</span> 
		<span>(32 items)</span> 
	</div>
```

As briefly mentioned in the previous section, a Module is a more discrete component of the page. It is your navigation bars and your carousels and your dialogs and your widgets and so on. This is the meat of the page. Modules sit inside Layout components. Modules can sometimes sit within other Modules, too. Each Module should be designed to exist as a standalone component. In doing so, the page will be more flexible. If done right, Modules can easily be moved to different parts of the layout without breaking.

When defining the rule set for a module, avoid using IDs and element selectors, sticking only to class names. A module will likely contain a number of elements and there is likely to be a desire to use descendent or child selectors to target those elements.

Module example

```css
.module > h2 {
    padding: 5px;
}

.module span {
    padding: 5px;
}
```

** Avoid element selectors **

Use child or descendant selectors with element selectors if the element selectors will and can be predictable. Using  `.module span`  is great if a span will predictably be used and styled the same way every time while within that module.

Styling with generic element

```html
<div class="fld">
    <span>Folder Name</span>
</div>

/* The Folder Module */
.fld > span {
    padding-left: 20px;
    background: url(icon.png);
}

```

The problem is that as a project grows in complexity, the more likely that you will need to expand a component’s functionality and the more limited you will be in having used such a generic element within your rule.

Styling with generic element

```html
<div class="fld">
    <span>Folder Name</span> 
    <span>(32 items)</span>
</div>

```

Now we are in a pickle. We don’t want the icon to appear on both elements within our folder module. Which leads me to my next point:

**_Only include a selector that includes semantics._  A span or div holds none**. A heading has some.

```html
<div class="fld"> 
	<span class="fld-name">Folder Name</span> 
	<span class="fld-items">(32 items)</span> 
</div>
```
By adding the classes to the elements, we have increased the semantics of what those elements mean and removed any ambiguity when it comes to styling them.

If you do wish to use an element selector, it should be within one level of a class selector. In other words, you should be in a situation to use child selectors.

The need for a new positioning context, for example, is likely to happen at either the layout level or at the root of a module.


## States Rules

For example, an accordion section may be in a collapsed or expanded state. A message may be in a success or error state.

States are generally applied to the same element as a layout rule or applied to the same element as a base module class.


```html
<div id="header" class="is-collapsed"> 
	<form> 
		<div class="msg is-error"> There is an error! </div> 
		<label for="searchbox" class="is-hidden">Search</label> 
		<input type="search" id="searchbox"> 
	</form> 
</div>
```
`is-collapsed` y `is-error` son reglas de estado

### Theme rules
A theme defines colours and images that give your application or site its look and feel.

Themes can affect any of the primary types. It could override base styles like default link colours. It could change module elements such as chrome colours and borders. It could affect layout with different arrangements. It could also alter how states look.

### Typography

Font rules will normally affect base, module and state styles. Font styles won’t normally be specified at the layout level as layouts are intended for positioning and placement, not for stylistic changes like fonts and colours.


### BEM

![](https://cdn-images-1.medium.com/max/1600/1*tBFD64u6_kmPVFNxjau17A.png)
  

```html
<div class="bloque">
		<ul class="bloque__list">
			<li class="bloque__list-item">
				<a class="bloque__list-item-link" href="#">Home</a>
			</li>
			<li class="bloque__list-item">
				<a class="bloque__list-item-link" href="#">Home</a>
			 </li>
			<li class="bloque__list-item--end">
				<a class="bloque__list-item-link" href="#">Home</a>	
			</li>
	</ul>
</div>
````


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

el typeof se usará bastante como en estos casos:

```js
1 + '2' // lo convierte a string y devuelve 2
```

```js
var count = 10
for (; count--;) console.log(count) // imprime de 9 a 0
```

### instanceOf
Ver instanceOf, se utiliza para objetos

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

## Enlaces

-  [guía de markdown](https://daringfireball.net/)

-  [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#html)



 > BOM leer esto por encima: https://developer.mozilla.org/es/docs/Web/API/Window
 > DOM leer por encima: https://developer.mozilla.org/es/docs/Acerca_del_Modelo_de_Objetos_del_Documento
 > https://developer.mozilla.org/en-US/docs/Web/Events
 > https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern
 > css dinner
 

