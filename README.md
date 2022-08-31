#CURSO PROFESIONAL DE GIT Y GITHUB mfriascos

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) ![](https://img.shields.io/github/release/pandao/editor.md.svg) ![](https://img.shields.io/github/issues/pandao/editor.md.svg) ![](https://img.shields.io/bower/v/editor.md.svg)


##Comandos básicos de git 

`$ git init`	Inicializa un repositorio en la carpeta donde se ejecuta 

`$ git add`		Añade los archivos específicos en el área de preparación(staging)

`$ git add .`	Se agregan todos los archivos que se hayan cambiado en la carpeta actual 

`$ git commit -m "commit description"`	Confirma los archivos que se encuentran en el área de preparación

`$ git commit -am "commit description`	Añade el staging area y hace un commit mediante.

`$ git status`	Ofrece una descripción de los estados de los archivos (Untracked)

`$ git rm (-r, filename)(-cached)`	Remueve los archivos del index

`$ git config`	Muestra todas las configuraciones posibles de git

`$ git config --global user.email tu@email.com`	configura tu email

`$ git config --global user.name "Tu Nombre"`	configura un nombre

`$ git config --list`	Lista las configuraciones

`$ git show`	Todos los cambios históricos realizados incluyendo cuales han sido las líneas de código o de texto

`$ git branch nombredelarama`   Crea una nueva rama

`$ git checkout nombredelarama` Se cambia de espacio de trabajo (rama)

Cuando se crean commits diferentes en cada rama y luego se fusionan se denomina **MERGE**

Para utilizar el comando Merge traigo los cambios que quiero que se ejecuten. Es decir la rama "Head" tiene un buen diseño y lo requiero en la rama main entonces utilizo 

`---> main`
`$ git merge head`

##GITHUB

`$ git remote add origin urldelrepositorioquecree`  Para traer y enviar cosas al servidor de GitHub

`$ git pull origin main --allow-unrelated-histories`    Para traer todo lo que se encuentra en el repositorio remoto y evitar errores. Se utiliza al inicio, luego, git pull origin main. 

`$ git push origin main`    Para enviar al repositorio remoto desde el repositorio local la rama main

Para trabajar en github se debería cambiar el nombre de la rama y se lo hace con 

`$ git branch -m master main`   Cambia el nombre de una rama, en este caso GitHub maneja Main en lugar de master 

Para problemas con git pull 

`$ git pull origin main --rebase`   Se utiliza cuando el primer pull no funciona 

###CONEXIÓN A GITHUB CON SSH

Se copia el enlace ssh y luego se ejecutan los siguientes comandos 

`$ git remote set-url origin urlssh`

Para trabajos o proyectos a remoto 

`$ git pull origin main`

`$ git push origin main`    Siempre después del commit

###TAG Y VERSIONES EN GIT Y GITHUB

`$ git tag -a numerodeversion -m "Comentario" numerodelcommitobtenidodegitlog`

`$ git tag` Muestra la lista de todos los Tags

`$ git show-ref --tags` Muestra a que commit está asignado

Para enviar a remoto el tag se hace 

`$ git push origin --tags`

Si se crea un tag errado

`$ git tag -d nombredeltag`

`$ git pull origin main`

`$ git push origin --tags`

`$ git push origin :refs/tags/nombredeltag`

###MANEJO DE RAMAS EN GITHUB

`$ git show branch` Muestra las ramas existentes y su historia

`$ git show-branch --all`

Para enviar una rama

`$ git checkout nombredelarama`

`$ git push origin nombredelarama`

###CREAR HEADER Y FOOTER

`$ git branch header`

`$ git push origin header`

`$ git push origin footer`

###CONFIGURAR MÚLTIPLES COLABORADORES EN UN REPOSITORIO DE GITHUB

Ingresa los colaboradores en las configuraciones del repositorio 

###FLUJO DE TRABAJO PROFESIONAL CON PULL REQUEST

Estado intermedio antes de hacer el merge

###CREANDO UN FORK, CONTRIBUYENDO A UN REPOSITORIO

se hace un fork, se toma una copia del repositorio y se clona. 

Se clona al repositorio local 

Se realizan cambios y luego un commit

###IGNORAR ARCHIVOS EN EL REPOSITORIO CON .GITIGNORE

.gitignore es una lista que se va a ignorar

Creo una archivo llamado de esa forma (.gitignore) y en él escribo * jpg si quiero ignorar todas las imágenes, por ejemplo, o /pictures/*.jpg
si quiero ignorar las imagenes de la carpeta pictures

###35/43: GIT REBASE: REORGANIZANDO EL TRABAJO REALIZADO

**REBASE** Reescribe la historia del repositorio, cambia la historia de donde comenzó la rama y sólo debe ser usado de manera local.
El rebase se lo hace desde la rama afectada, no desde la rama main. 

`---> otra rama`
`$ git rebase main` Primero se hace rebase hacia la rama principal y luego hacia la rama secundaria desde main

`--->main`
`$ git rebase otrarama`

--En Conlusión un git rebase es una forma de hacer cambios silenciosos en otras ramas y volver a pegar una historia de esa rama a una rama anterior haciendole un rebase.--

###36/43 GIT STASH: GUARDAR CAMBIOS EN MEMORIA Y RECUPERARLOS DESPUÉS

**STASHED** Nos sirve para guardar cambios para después, es una lista de estados que nos guarda algunos cambios de rama sin perder el trabajo que todavía no guardamos en un commit.

`--->main`
`$ git stash`   Vuelve al estado anterior, esto funciona siempre y cuando no se haga un commit, esto también guarda el cambio realizado, como un punto de restauración hacia el estado editado.

`$git stash pop`    Vuelve al estado editado.

`$ git stash list`  Muestra los stash temporales guardados.

`$ git stash branch otrarama`   Si quiero poner esos cambios realizados en otra rama se ingresa este comando, automaticamente se crea esa rama

`$ git stash drop`  Para borrar el git stash 

###37/43 GIT CLEAN: LIMPIAR TU PROYECTO DE ARCHIVOS NO DESEADOS 

`$ git clean --dry-run` Muestra los archivos que se van a borrar 

`$ git clean -f`    Borra los archivos no deseados 

`$ git clean -df`   Borra las carpetas

###38/43 GIT CHERRY-PICK TRAER COMMITS VIEJOS AL HEAD DE UN BRANCH

`--->main`
`$ git cherry-pick hashdelcommit`   Se inserta el hash del commit que quiero traer Esto se lo hace en la rama main

###39/43 GIT RESET Y REFLOG:ÚSESE EN CASO DE EMERGENCIA 

Git guarda todos los cambios aunque decidads borarlos, al borrar un cambio lo que estás haciendo sólo es actualizar la punta del branch, para gestionar estas puntas existe un mecanismo llamado registros de referencia o reflogs. 

`--->main`
`$git reflog`   Se busca el hash correcto donde no hayan cambios no deseados

`$git reset --HARD hash`    Regresa al punto de restauración y desaperecen todos loscambios realizados, incluso los commits. 

###40/43 RECONSTRUIR COMMITS EN GIT CON AMEND

`$ git commit --amend`  Los cambios que se hicieron los pega al commit anterior No crea un commit nuevoRegresa al punto de restauración y desaperecen todos los cambios realizados, incluso los commits. 

###40/43 RECONSTRUIR COMMITS EN GIT CON AMEND

`$ git commit --amend`  Los cambios que se hicieron los pega al commit anterior No crea un commit nuevo

###41/43 BUSCAR EN ARCHIVOS Y COMMITS DE GIT CON GREP Y LOG 

`$ git grep color`  Busca donde se usó color 

`$ git grep la` Donde se usó la palabra "la"

`$ git grep -n color`   En qué lineas se usó la plabra color 

`$ git grep -c la`  Cuantas veces se usó la plabra "la"

`$ git grep -c platzi`  Cuantas veces se usa la plabra Platzi 

`$ git grep -c "<p>"`   Cuantas veces se utilizó la etiqueta "<p>"

`$ git log -S "cabecera"`   Cuantas veces se usó la plabra cabecera en todos los commits.

*---> grep: para los archivos.*
*---> log: para los commits*

###42/43 COMANDOS Y RECURSOS COLABORATIVOS EN GIT Y GITHUB

`$ git shortlog -sn`    Muestra cuantos commit han hecho cada miembro del equipo 

`$ git shortlog -sn --all`  Muestra cuantos commit han hecho cada miembro del equipo hasta los que han sido eliminados

`$ git shortlog -sn --all --no-merge`   Muestra cuantos commit han hecho cada miembro quitando los eliminados sin los merges

`$ git blame ARCHIVO -Llinea_inicial,linea_final` Muestra quien hizo cada cosa por linea indicandole desde que línea ver por ejemplo -L35,50.
`$ git branch -r`   Se muestran todas las ramas remotas 
`$ git branch -a`   Se muestran todas las ramas tanto locales como remotas