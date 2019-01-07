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
- `git commit -m "initial import"` "initial import" típico 1er mensaje para GIT
- `git show <id del log>` para ver los cambios que se han guardado
- `git checkout index.html` recuperar archivo index.html
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
- `git push --set-upstream origin develop`

### Git Flow

- **Rama master**: cualquier commit que pongamos en esta rama debe estar preparado para subir a producción
- **Rama develop**: rama en la que está el código que conformará la siguiente versión planificada del proyecto

Cada vez que se incorpora código a master, tenemos una nueva versión.

Además de estas dos ramas, Se proponen las siguientes ramas auxiliares:

- **Feature**: Estas ramas se utilizan para desarrollar nuevas características de la aplicación que, una vez terminadas, se incorporan a la rama develop. Se originan y se incorporan siempre a la/desde rama develop.
- **Release**: En estas ramas se hacen los últimos ajustes y se corrigen los últimos bugs antes de pasar el código a producción incorporándolo a la rama master. Se originan desde la rama develop pero se integran tanto en master como en develop.
- **Hotfix**: Esas ramas se utilizan para corregir errores y bugs en el código en producción. Funcionan de forma parecida a las Releases Branches, siendo la principal diferencia que los hotfixes no se planifican. Se originan desde la rama Master y se integran tanto en master como en develop.