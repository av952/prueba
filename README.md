![Imgur](https://i.postimg.cc/dVNfQQdr/color.png)


## Links

[Git stash](https://www.atlassian.com/es/git/tutorials/saving-changes/git-stash)

[Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)


Para ver en que carpeta estamos usamos

    pwd

Para navegar a una carpeta usamos

    cd

Para listar los archivos usamos

    ls

Para mostarr todos los archivos inluyendo los ocultos dentro de una lista donde **a** hace referencia a los archivos ocultos y **l** me los lista

    ls -al

Para limpiar la consola podemos utilizar

    Ctrl+l

    clear

Para regresar a la carpeta anterior

    cd ..

Para poder auto completar usamos

    cd + <La primera letra del archivo> + TAB

    cd + <un par de letras mas del nombre> + TAB

Crear carpeta

    mkdir <nombre>

Crear archivo

    touch <nombre archivo con extencion>

Ver el contenido de un archivo

    cat vacio.txt

Ver todos los comandos escritos ultimamente

    history

El comando anterior nos va alanzar una lista de comandos con un numero a la izquierda, para poder acceder a dichos comandos utilizamos:

    !<#>

Eliminar archivo

    rm 


## GIT

Ver estatus

    git status

Añadir elementos a git 

    git add <nombre del archivo>

Eliminar un elemento de git

    git rm <nombre>

    git rm --cached <nombre>
    //Con el --cached lo eliminamos de la memoria ram

Para enviar los cambios al repositorio usamos

	git commit -m 'mensaje'

## Configurar GIT

	git config

Para ver la configuración por defecto y las cosas que lehacen falta

	git config --list

Ver donde se almacenan las configuraciones

	git config --list --show-origin

Para usar la version acortada de un comando va con un solo  -  para usar la palabra se usa   - -

Mostrar los cambios que ha tenido un archivo

	git show <nombre>

Comparar archivos

	git diff <hash commit> <hash commit>

Mirar el esado actual mas detallado

	gitgit log --stat


Para resetear y volver a un punto anterior en el tiempo usamos

	git reset
	git reset --hard #para regresar todo a sus estado anterior 
	git reset -soft #para mantener los elementos a los que le hemos echo git add

Para Regresar en el tiempo y modificar una parte del código dentro de un código anterior:

	git checkout <hash del commit>

Con eso volveriamos a como estaba el programa en ese momento y podriamos crear una nueva rama para modificar desde ese punto de la siguiente manera

	git switch -c <nombreRama>

Evitar que los ultimos cambios se envien, es decir aquellos archivos que hayamos agregado con **git add .** ya no seran agregados para el commit que vayamos a hacer.  

	git reset HEAD <nombreArchivo>

## repositorios remotos

Para traer los archivos de un repositorio remoto

	git clone <url>
	git fetch #traer los cambios que se han realizado ha mi repositorio local
	git merge #copiarlo en mis archivos fusionando lo que tengo con lo que trajo
	
	git pull #combina el fetch con el merge

Para crear la rama desde la rama actual

	git branch <nombre>

Intercambiar entre ramas

	git checkout <nombre>

Para realizar la unión entre nuestras ramas, lo primero es estar ubicados en la rama a la que vamos a traer la información, digamos si estoy en master quiero traer la rama cabecera, pero no tendría sentido hacerlo al contrario.

	git merge <nombreRama>

Para hacer el*merge* y eliminar la rama en caso de que ya no la necesitemos usamos:

	git merge -d <nombreRama>


Recuperar la rama eliminada

	git fsck --full --no-reflog | grep commit
	git branch [branchName] [SHA1]
	ó
	git checkout <hash>


Para revertir los cambios antes de haber echo comit de los archivos traidos de la otra rama podemos usar:

	git restore .
	git reset --hard

Cambiar el nombre de una rama

	git branch -m new-name

Cambiar el nombre de otra rama

	git checkout master
	git branch -m old-name new-name


## Solución de conflictos

Pueden existir confliuctos cuando se cambia el mismo valor en dos ramas diferentes, cuando esto ocurre **git** nos muestra la zona afectada y tenemos que elegir una opción.


[========]

## Uso de GITHUB

Teniendo un repositorio remoto en github (en blanco)

	git remote add origin <url-gitHub>

Si utilizamos el comando  `git remote` podemos notar que noara tenemos algo llamado **origin** y si usamos `git remote -v` nos va mostrar dos lineas de texto una de las cuales nos muestra que tenemos un archivo para hacer **fetch**(traernos cosas) y un **push** (enviar cosas)

	git pull origin <nombre Rama> --alow-unrelated-histories
	#con esto logramos que no nos de conflicto al traer una rama de github y 				fucionarla con  una rama local

	git pull origin <nombreRama>

Por ultimo para que se suban los archivos:

	git pull origin <nombreRama>

## Llaves públicas y llaver privadas

### SSH

Las llaves SSH no se generan por repositorio si no por persona, por lo que deben ser creadas desde la carpeta home para eso accedeemos a `cd`  y ahi nos llevara a la carpeta raiz donde podremos ejecutar el comando para crear las llaves

	ssh-keygen -t rsa -b 4096 -C '<correoGitHub>'

Luego tendremos que saber para windows y linux si esta corriendo el servidor de ssh

	eval $(ssh-agent -s)

Ahora necesitamos añadirla para que se pueda teneracceso a esa clave privada

	ssh-add ~/.ssh/id_rsa
	#con  ~ lo que hacemos es acortar el camino para encontrar la dirección especificada


### TAGS

Los tags nos sirven para hacer referencia a un punto especifico en el tiempo, como puede ser un cambio importante en nuestro archivo o una nueva versión. Existen dos tipos de etiquedado las **ligeras** y las **anotadas** para crear un tag ligero es tan facil como:

	git tag <tagname>

Para crear un tag anotado que es el que trae más información

	git tag -a v1.4 -m "my version 1.4"


### Git rebase

Con git rebase fusionamos una rama por ejemplo la rama *bug-fix* con la rama *main* pero eliminando todo rastro de la anterior rama como si nunca hubiera estado ahí.

		git rebase <nombreRama>


1[img](https://i.postimg.cc/jjT9QBj2/Untitled-5d59eeed-f90a-4eed-b893-dc32de72e622.jpg)



### Git stash 

Con esta funcionalidad es posible hacer un cambio entre ramas sin necesidad de guardar los cambios, pero hay que tener en cuenta que lo que hayas modificado se va a deshacer hasta que tu recuperes los datos almacenados en el **stash**

	#almacenar los datos que tienen seguimiento
	git stash

	#Almacenar los datos que aún no tienen seguimiento
	git stash -u 

	#Almacenar los cambios de los archivos ignorados
	git stash -a || --all

	#crear una nueva rama a partir del estash
	git stash branch

	#limpiar el stash
	git stash drop

	#Limpiar todos los stash
	git stash clear 

	#recuperar los datos almacenados
	git stash pop


### Git clean

Con esta propiedad es posible limpiar tu proyesto de archivos no deseados. Tener en cuenta que este comando solo borrara archivos nuevos.

	#Hace una previsualización de los archivos a borrar
	git clean --dry-run

	#Elimina los archivos
	git clean -f


### Git cherry-pick: traer commits viejos al head de un branch

Con esta funcionalidad podemos regresar a un punto anterior en el tiempo para fucionar con la rama en la que estemos trabajando sin importar que el commit sea de otra rama. esta practica no es muy recomendada debido a que puede causar conflictos.

	git cherry-pick commitSha


### Git reset y Reflog

Por medio de **reflog** podemos acceder a toda la historia para poder volver a un punto especifico antes de haber echo algo mal utilizando el *hash* que nos dan para pasarselo a *reseet*

	git reset --hard <hash>

### Git amend

Con esta funcionalidad logramos reutilizar  el ultimo commit con la nueva información actualizada.

	git commit --amend


### Buscar en archivos y commits de Git con Grep y log

git grep color -->use la palabra color
git grep la --> donde use la palabra la
git grep -n color–> en que lineas use la palabra color
git grep -n platzi --> en que lineas use la palabra platzi
git grep -c la --> cuantas veces use la palabra la
git grep -c paltzi --> cuantas veces use la palabra platzi
git grep -c “<p>”–> cuantas veces use la etiqueta <p>

git log-S “cabecera” --> cuantas veces use la palabra cabecera en
todos los commits.

grep–> para los archivos
log --> para los commits.

### Comandos y recursos colaborativos en Git y GitHub

git shortlog -sn = muestra cuantos commit han hecho cada miembros del equipo.
git shortlog -sn --all = muestra cuantos commit han hecho cada miembros del equipo hasta los que han sido eliminado
git shortlog -sn --all --no-merge = muestra cuantos commit han hecho cada miembros quitando los eliminados sin los merges
git blame ARCHIVO = muestra quien hizo cada cosa linea por linea
git COMANDO --help = muestra como funciona el comando.
git blame ARCHIVO -Llinea_inicial,linea_final= muestra quien hizo cada cosa linea por linea indicándole desde que linea ver ejemplo -L35,50
**git branch -r **= se muestran todas las ramas remotas
git branch -a = se muestran todas las ramas tanto locales como remotas


### revisar ramas locales y las ramas remotas

	#mirar las ramas remotas 
	git branch -r

	#mirar todas las ramas
	git branch -a










