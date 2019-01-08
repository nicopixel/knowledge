## console commands

- `pwd` path to working directory
- `carpeta /` carpeta raíz
- `cd` change directory
- `rm -rf git-demo/` la f significa force
- `cd /nico/desktop` cuidado con la barra inicial del todo que indica que debe empezar a buscar desde el inicio por ejemplo así: cd ../nico/ el último ejemplo es con rutas absolutas
- `mkdir folder-name`
- `drwxr-xr-x  2 nico  staff  68  7 ene 12:00 lab` usuario que ha creado el archivo y grupo (staff) que ha creado el archivo
- `cp file1 file2` copiar file1 a file2
- `cp -r file2/ folder3`
- `mv file2 /file2` mover file2 a la carpeta /file2
- `mv folder3/file2 folder3/file3` cambiar el nombre de file2 a file3
- `tree` permite ver en forma de árbol la estructura de ficheros y carpetas. Hay que instalarlo
- `man <command-name>` ver información de cualquier comando
- `Cmd + K` limpiar pantalla
- `Ctrl + L` limpiar pantalla
- `chmod 664 file3` cambiar permisos del achivo file3
- `echo "ciao mondo" > file4` echo enviar algo a consola y el símbolo > es enviar el contenido a un fichero
- `history` ver el historial de comandos que has realizado
- `find . -name file2` buscar un fichero o carpeta
- `find . -type` 

### `grep` command. One of the most useful commands on Linux 
- `grep 'word' filename` search any line that contains the word in filename on Linux
- `grep -i 'bar' file1` a case-insensitive search for the word ‘bar’ in Linux and Unix
- `grep -R 'foo'` search all files in the current directory and in all of its subdirectories in Linux for the word ‘foo’
- `grep -c 'nixcraft' frontpage.md` search and display the total number of times that the string ‘nixcraft’ appears in a file named frontpage.md
- `grep -r "192.168.1.5" /etc/` search recursively i.e. read all files under each directory for a string “192.168.1.5”

___
### editor nano

- `ctrl + x`  salir
- `ctrl + o`  guardar + ENTER
___
### Permisos - chmod

- grupo 1 - rwx - usuario que ha creado 
- grupo 2 - r-x - grupo
- grupo 3 - r-x - otros grupos

Transformación de binario a decimal con tres dígitos binarios puedo contar de 0 a 7

Cambiar a que el grupo puede escribir el archivo file3 
- `-rw-r--r--  1 nico  staff   25  7 ene 12:18 file3`
- `chmod 664 file3`
- `rw-rw-r--  1 nico  staff   25  7 ene 12:18 file3`
___

### Otros

Todos los proyectos deben tener README.md. .md es formato markdown

- Investigar use cases en el readme.md
- y leer la guía de markdown en https://daringfireball.net/
- Crear un archivo README.MD para cada proyecto

## GIT
- `git commit -m "initial import"` "initial import" típico 1er mensaje para el primer commit
- `git show <id del log>` para ver los cambios que se han guardado en un ID en específico
- `git checkout index.html` recuperar archivo index.html por ejemplo por si se ha borrado
- `git diff` ver los cambios en específico
- Remember: los commits solo comitean lo que esté en staging (git add .)
- `git reset --hard HEAD` recupera el último commit de la rama donde estoy trabajando. Otra forma de hacerlo con un fichero concreto `git rm --cached index.html`
- Al crear una nueva rama se copia desde el último commit desde la rama donde estamos
- `git branch develop` crear rama nueva
- `git remote add origin https://github.com/nicopixel/git-demo.git`
- Origin es la rama remota por defecto
- `HEAD` significa el último commit
- `git log --graph` ver detalles de la rama actual
- `git log --graph --all` ver detalles de todas las ramas
- merge hace un auto commit internamente
- `git push -u origin master` subir rama master al remoto por defecto (origin)
- `git push -u origin develop` subir rama develop al remoto por defecto (origin)
- `git push --set-upstream origin develop` se hace una única vez para cada rama. Es para tener las ramas sincronizadas entre remoto y local. También podemos indicar el nombre de la rama en remoto, en nuestro caso en develop
- `git pull` integrar el estado actual de remote en local. Por ejemplo, si tenemos cambios que queremos subir pero que pueden sobrescribir el código en remoto debemos hacer primero un GIT pull
- `git branch -d feature/login` borrar rama en LOCAL llamada feature/login
- `git branch -D feature/background-pink` borrar rama en REMOTO llamada feature/background-pink
- `git checkout -b feature/cian` crear rama y cambiarse a ella
- `git push origin --delete feature/body-border` borrar la rama feature/body-border de REMOTO
- `git add .` esto sube todos los archivos en el directorio antual pero no es buena idea ya que puede subir archivos de otroas personas. Lo recomendado es subir los archivos uno a uno
- `git clone https://github.com/nicopixel/skylab-bootcamp-201901` clonar repositorio. Cuidado porque se clonan todas las ramas del repo de remoto. Cuando hacemos un `git branch` en local NO vemos todas las ramas pero igualmente se puede cambiar a la rama aunque no la veamos

**La rama MASTER no se toca**

**Tagear versiones**
Antes de entregar al cliente hay que tagear `git tag v1.0.0` y subir a remoto los tags por medio de `git push --tags` en este caso no se generan commits en remoto, se generan únicamente los tags.

Los tags se utilizan para indicar las versiones:

Los números de las versiones se indican con la sintaxis de `1.2.3`
- `1` - indica cambios mayores que implican comportamiento profundo de la aplicación
- `2` - cambios menores
- `3` - cambios ligeros

**Modo Folk**
**Útil para trabajar proyectos open sources**

Forkear es hacer una copia de un repo dentro de mi propio espacio de Github. Una vez 'forkeado' se trabaja en los cambios del código. Pasos:

1. Forkeamos el proyecto original
2. Hacer un clone de mi repositorio forkeado
3. Se hacen los trabajos en local creando una rama 
4. Hacemos push a mi repositorio forkeado (`git push --set-upstream origin feature/fix-readme`)
5. En REMOTO aplicamos Pull-request contra el proyecto original

No hay una regla definida para definir qué cambio pertenece a cada categoría

### Pull Request (PR)

Pull request es un método para comparar dos ramas diferentes de diferentes usuarios y ver si hay conflictos antes de realizar un merge. 

Es un buen método para comparar, comentar y trabajar en el código. Se puede comentar en github de manera global y en cada línea.

Una vez aprobada la rama del compañero podemos hacer el Merge Pull Request.

No olvidar que tenemos que subir la rama de feature/nombre-rama a remoto. No vale con hacer git push, la primera vez que subimos la rama a remoto, tenemos que hacer un `git push --set-upstream origin feature/body-border`

### Git Flow

- **Rama master**: cualquier commit que pongamos en esta rama debe estar preparado para subir a producción
- **Rama develop**: rama en la que está el código que conformará la siguiente versión planificada del proyecto

Cada vez que se incorpora código a master, tenemos una nueva versión.

Además de estas dos ramas, Se proponen las siguientes ramas auxiliares:

- **Feature**: Estas ramas se utilizan para desarrollar nuevas características de la aplicación que, una vez terminadas, se incorporan a la rama develop. Se originan y se incorporan siempre a la/desde rama develop.
- **Release**: En estas ramas se hacen los últimos ajustes y se corrigen los últimos bugs antes de pasar el código a producción incorporándolo a la rama master. Se originan desde la rama develop pero se integran tanto en master como en develop.
- **Hotfix**: Esas ramas se utilizan para corregir errores y bugs en el código en producción. Funcionan de forma parecida a las Releases Branches, siendo la principal diferencia que los hotfixes no se planifican. Se originan desde la rama Master y se integran tanto en master como en develop.