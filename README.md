# Comandos básico consola

**$ pwd** --> muestra la ruta donde me encuentro

**$ cd** o **$ cd \~**  --> desde donde esté me lleva a mi "home" de git en local. *\~* es como una variable que contiene la ruta de mi HOME.

**$ clear** --> limpia pantalla

**$ ls** --> muestra los ficheros de la carpeta donde estoy (comoel DIR de MS-DOS)

**$ ls -al** --> muestra los ficheros uncluyendo los ocultos (con -a) y mostrando los detalles (con -l)




# Comandos básico GIT
**$ git init** --> inicializa un repositorio (la carpeta donde estés).

**$ git add biografía.txt** --> añade cambios del fichero a STAGING (temporal) del repositorio  de git.

**$ git commit -m "versión 1"** --> añade cambios de STAGING al  repositorio local de git.

**$ git add .** --> añade todo lo que se haya modificado en esa carpeta.

**$ git commit -m "cambios versión 1"** --> añade nuevos cambios de STAGING al repositorio local de git.

**$ git status** --> muestra los cambios pendientes antes del commit.

**$ git show** --> muestra el detalle del cambio del commit en el que estamos ubicados.

**$ git log biografía.txt** --> muestra el histórico de cambios del archivo indicado.

**$ git push** --> lo manda a un repositorio remoto.

**$ git pull** --> lo trae de un repositorio remoto.


# Instalación
Te lo bajas de https://git-scm.com/downloads

**$ git --version** --> Para comprobar que está bien instalado.

**$ git checkout** --> sincronizas la rama master: todos los cambios, solo ciertos cambios, solo los hechos a un archivo...


# Ramas
Son "lineas temporales" que se crean para poder trabajar independientemente a la línea principal master.

Las más comunes 
* master --> está en todos los repositorios, es la rama principal
* development --> para experimentos
* hotfix --> para parches

Cuando juntas una rama hacia el master el la accion (y el comeando) se llama "merge"


# Configurar Git
**$ git config** --> muestra HELP del comando "config"

**$ git config --list** o **-l** --> te salen los parámetros configurados

**$ git config --global user.name "CarlosRojasF"** --> Agrega nombre al repositorio.

**$ git config --global user.email "crojasf@gmail.com"** --> Agrega mail al repositorio.


# Analizar cambios en los archivos de tu proyecto con Git
**$ git log historia.txt** --> te muestra de descripciónde los cambios en el archivos

**$ git show historia.txt** --> te muestra los cambios en el archivo

**$ git diff <HASHcommit1> <HASHcommit2>** --> saca las diferencias entre 2 commits

**$ gif diff** --> sin ningún parámetro más muestra las diferencias entre lo queestá en staging y el último commit 

# Volver en el tiempo en nuestro repositorio utilizando branches y checkout

**$ git reset <commit> --hard** --> vuelve al commit que le digamos cambiando los ficheros.

**$ git reset <commit> --soft** --> vuelve al commit que le digamos SIN cambiar los ficheros pero los cambios en STAGING.

**$ git checkout <commit> historia.txt** --> trae el fichero que hubiera en ese commit.

**$ git checkout master historia.txt** --> trae el fichero que haya en ese momento en la versión más reciente de la rama master.


# Aclaración entre Git reset vs. Git rm
**$ git rm --cached** --> Elimina los archivos del área de Staging y del próximo commit pero los mantiene en nuestro disco duro.

**$ git rm --force** --> Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro dela existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

**$ git reset** --> Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás. Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones:


# Flujo de trabajo básico con un repositorio remoto
**$ git clone url_del_servidor_remoto** --> Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git

**$ git pull** --> Básicamente, git fetch (trae actualizaciones del servidor remoto y las guarda en el repositorio local) y git merge (combina los últimos cambios en nuestro directorio de trabajo) al mismo tiempo.


# Introducción a las ramas o branches de Git
Cuando hacemos una rama, hacemos una copia del último commit en otro lado, y estos cambios no los ve la rama master hasta que hacemos un merge.

**$ git branch cabecera** --> crea una rama llamada "cabecera".

**$ git checkout cabecera** --> te mueves a la rama cabecera. Mueve el "HEAD" a la rama cabecera, que equivale a ponerte en el directorio de trabajo todos los ficheros de esa rama.

**$ git status** --> te dice en qué rama estás.


# Fusión de ramas con Git merge
Merge lo que hace es traer los cambios de la rama que se indique y la fusiona con los cambios de la rama en la que estoy donde ejecuto el comando. generalmente se hace merge desde master.

**$ git checkout master** --> pones el HEAD en la última versión de la master porque aquí quiero traer lo de cabecera.

**$ git merge cabecera** --> fusiona todos los ficheros de cabecera en master.

**$ git branch** --> lista el listado de ramas


# Solución de conflictos al hacer un merge
AL hacer unmerge, y una misma línea tiene 2 valores diferentes, muestra el error así
```
<<<<<<< HEAD
		Cambios de la rama actual
=======
 		Cambios de la rama que traigo con merge
 >>>>>>> cabecera
```
En visualcode te muestra un menú justo arriba para ejecutar el cambio que quieras y quitar estas líneas.


# Uso de GitHub

* https://github.com/
* Creamos cuenta en GitHub
* Creamos repositorio online
* Copiamos la URL de mi repositorio creado

En Master ejecutamos

**$ git remote add origin url_de_mi_repositorio_en_github** --> crea en "origin" el enlace a mi repositorio online.

**$ git remote -v** --> muestra las acciones que podemos realizar con "origin", que es el "fetch" para traer cosas y el "push" para enviar cosas.

**$ git push origin master** --> envía la rama master de origin a master de repositorio y directorio local.

Si da error _fatal: refusing to merge unrelated histrories_ es porque el histórico de commits de repositorio online (origin) no coincide con el del repositorio local. 

**$ git push origin master --allow-unrelated-histories** --> soluciona conflicto de historias al enviar la rama master de origin a master de repositorio y directorio local.


# Configurar tus llaves SSH en local
Crear una llave por cada equipo físico que tengas.

**$ cd** --> Navegar a la ruta de mi HOME de git para crear aquí mi clave SSH

**$ git config --global user.email "crojasf@gmail.com"** --> Configurar el git local para que el email configurado sea el mismo que tu cuenta de GITHUB.

**$ ssh-keygen -t rsa -b 4096 -C "crojasf@gmail.com"** --> comando para generar clave. "-t" para escoger el algoritmo "rsa". "-b" para elegir la complejidad. "-C" (mayúsculas) para el email.

Pregunta lugar donde guardar la clave, por defecto guarda en *c/Users/MI_USUARIO_WINDOWS/.ssh/id_rsa*. Pulsamos INTRO.

Pregunta una contraseña adicional de texto para darle una capa más de seguridad. No es obligatorio.

En la carpeta *.ssh* dentro de HOME de git se guardan las llaves en ficheros llamado **id_rsa** para la privada y **id_rsa.pub** para la pública. 

**$ eval $(ssh-agent -s)** --> evaluar si el servicio de llaves SSH está activado en el sistema. da como resultado algo como *Agent pid 0000* que significa que está activo.

**$ ssh-add \~/.ssh/id_rsa** --> Agregar la llave privada al sistema. IMPORTANTE: se debe indicar la tuta exacta de la llave, por eso se pone el "\~" delante.


# Conexión a GitHub con SSHH
En GitHub > Perfil > Settings > SSH and GPG keys agregamos las clave pública SSH de mi equipo.

En el ordenador cambiaremos la dirección de "origin" para que en vez de HTTPS sea el SSH

**$ git remote set-url origin git@github.com:crojasf/hyperblog.git** --> cambiamos la la "url" de origin por el ssh key.

**$ git remote -v** --> para ver la nueva "url".













