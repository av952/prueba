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








