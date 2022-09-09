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


