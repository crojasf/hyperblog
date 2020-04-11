# Comandos básico
$ git init --> inicializa un repositorio (la carpeta donde estés).
$ git add biografía.txt --> añade cambios del fichero a STAGING (temporal) del repositorio  de git.
$ git commit -m "versión 1" --> añade cambios de STAGING al  repositorio local de git.
$ git add . --> añade todo lo que se haya modificado en esa carpeta.
$ git commit -m "cambios versión 1" --> añade nuevos cambios de STAGING al repositorio local de git.
$ git status --> muestra los cambios pendientes antes del commit.
$ git show --> muestra el detalle del cambio del commit en el que estamos ubicados.
$ git log biografía.txt --> muestra el histórico de cambios del archivo indicado.
$ git push --> lo manda a un repositorio remoto.
$ git pull --> lo trae de un repositorio remoto.

# Instalación
Te lo bajas de https://git-scm.com/downloads
$ git --version --> Para comprobar que está bien instalado.
$ git checkout --> sincronizas la rama master: todos los cambios, solo ciertos cambios, solo los hechos a un archivo...

# Ramas
master --> está en todos los repositorios, es la rama principal
development --> para experimentos
hotfix --> para parches

Cuando juntas varias ramas hacia el master se llama merge

# Configurar Git
$ git config --> te dice cómo funciona
$ git --list --> te salen los parámetros configurados
$ git config --global user.name "CarlosRojasF"
$ git config --global user.email "crojasf@gmail.com"

# Analizar cambios en los archivos de tu proyecto con Git
$ git log historia.txt --> te muestra de descripciónde los cambios en el archivos
$ git show historia.txt --> te muestra los cambios en el archivo
$ git diff <HASHcommit1> <HASHcommit2> --> saca las diferencias entre 2 commits
$ gif diff --> sin ningún parámetro más muestra las diferencias entre lo queestá en staging y el último commit 

# Volver en el tiempo en nuestro repositorio utilizando branches y checkout
$ git reset <commit> --hard --> vuelve al commit que le digamos.
$ git checkout <commit> historia.txt --> trae el fichero que hubiera en ese commit.
$ git checkout master historia.txt --> trae el fichero que haya en ese momento en la versión más reciente de la rama master.


# Aclaración entre Git reset vs. Git rm
$ git rm --cached
Elimina los archivos del área de Staging y del próximo commit pero los mantiene en nuestro disco duro.

$ git rm --force
Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro dela existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

$ git reset
Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás. Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones:


# Flujo de trabajo básico con un repositorio remoto
$ git clone url_del_servidor_remoto
Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git
$ git pull -> Básicamente, git fetch (trae actualizaciones del servidor remoto y las guarda en el repositorio local) y git merge (combina los últimos cambios en nuestro directorio de trabajo) al mismo tiempo.

# Introducción a las ramas o branches de Git
Cuando hacemos una rama, hacemos una copia del último commit en otro lado, y estos cambios no los ve la rama master hasta que hacemos un merge.

$ git branch cabecera --> crea una rama llamada "cabecera".
$ git checkout cabecera --> te mueves a la rama cabecera. Mueve el "HEAD" a la rama cabecera, que equivale a ponerte en el directorio de trabajo todos los ficheros de esa rama.
$ git status --> te dice en qué rama estás.

# Fusión de ramas con Git merge
Merge lo que hace es traer los cambios de la rama que se indique y la fusiona con los cambios de la rama en la que estoy donde ejecuto el comando. generalmente se hace merge desde master.
$ git checkout master -> pones el HEAD en la última versión de la master porque aquí quiero traer lo de cabecera.
$ git merge cabecera -> fusiona todos los ficheros de cabecera en master.
$ git branch -> lista el listado de ramas

