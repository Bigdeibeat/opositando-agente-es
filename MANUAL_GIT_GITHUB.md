# Manual de uso: trabajar en local y guardar en GitHub

Este manual explica el sistema que vamos a usar para trabajar la web en tu ordenador y subir los cambios a GitHub solo cuando te gusten.

Tu carpeta local:

```text
C:\Users\santa\Documents\OpositandoCodex
```

Tu repositorio en GitHub:

```text
https://github.com/Bigdeibeat/opositando-agente-es
```

La idea es conectar ambas cosas para que esta carpeta sea la copia de trabajo local del repo.

## La idea general

Git es el sistema que guarda el historial de cambios de un proyecto.

GitHub es la web donde se guarda una copia online del proyecto.

El flujo normal seria:

```text
Editar archivos en local
Revisar la web en el navegador
Guardar los cambios con Git
Subirlos a GitHub
```

En otras palabras:

- Local: donde trabajamos y probamos.
- Git: el historial de cambios.
- GitHub: la copia online del proyecto.

## Por que conectar la carpeta local al repo

Ahora mismo la carpeta local tiene los archivos de la web, y el repo de GitHub tambien tiene esos archivos.

Lo correcto es conectar esta carpeta local con el repo, para evitar tener dos copias distintas.

Asi podremos hacer cambios aqui, probarlos, y cuando esten bien subirlos a:

```text
Bigdeibeat/opositando-agente-es
```

## Comandos principales

### git init

```powershell
git init
```

Convierte la carpeta actual en un repositorio Git.

Solo hay que hacerlo una vez por carpeta. Crea una carpeta oculta llamada `.git`, que es donde Git guarda el historial y la configuracion.

No sube nada a GitHub. Solo activa Git en local.

### git remote add origin

```powershell
git remote add origin https://github.com/Bigdeibeat/opositando-agente-es.git
```

Le dice a Git cual es el repositorio de GitHub conectado a esta carpeta.

`origin` es el nombre habitual que se usa para referirse al repo remoto.

Despues de esto, Git sabe que esta carpeta local debe sincronizarse con ese repo de GitHub.

### git remote -v

```powershell
git remote -v
```

Muestra que repositorio remoto esta conectado.

Sirve para comprobar que la carpeta apunta al repo correcto antes de subir nada.

### git status

```powershell
git status
```

Muestra el estado actual del proyecto.

Te dice cosas como:

- Que archivos se han cambiado.
- Que archivos son nuevos.
- Que archivos estan preparados para guardar.
- Si hay cambios pendientes de commit.

Este comando no cambia nada. Solo informa.

Es el comando mas seguro y mas util para comprobar que esta pasando.

### git add

```powershell
git add index.html
```

Prepara un archivo concreto para guardarlo en el proximo commit.

Tambien se puede preparar todo:

```powershell
git add .
```

El punto significa "todos los cambios de esta carpeta".

`git add` todavia no guarda definitivamente el cambio. Solo lo deja preparado.

### git commit

```powershell
git commit -m "Mejora la pagina de inicio"
```

Guarda los cambios preparados en el historial local de Git.

Cada commit es como una foto del proyecto en un momento concreto.

El texto entre comillas es el mensaje del commit. Debe explicar brevemente que se cambio.

Ejemplos:

```powershell
git commit -m "Actualiza textos del hero"
git commit -m "Mejora estilos responsive"
git commit -m "Corrige enlaces del temario"
```

### git push

```powershell
git push origin main
```

Sube los commits locales a GitHub.

Este es el paso que actualiza el repo online.

Antes de hacer `push`, conviene revisar:

```powershell
git status
```

### git pull

```powershell
git pull origin main
```

Trae a tu carpeta local los cambios que haya en GitHub.

Se usa cuando alguien ha cambiado el repo desde otro sitio, o cuando se quiere asegurar que la copia local esta al dia.

### git fetch

```powershell
git fetch origin main
```

Consulta GitHub y descarga informacion de los cambios remotos, pero no mezcla esos cambios automaticamente con tus archivos.

Es mas prudente que `git pull` cuando solo queremos comprobar que hay en GitHub.

### git branch -M main

```powershell
git branch -M main
```

Renombra la rama local actual a `main`.

GitHub suele usar `main` como rama principal. Este comando deja la carpeta local con el mismo nombre de rama que el repo online.

## Flujo recomendado para nuestra web

### 1. Antes de trabajar

Comprobar estado:

```powershell
git status
```

Si todo esta limpio, podemos trabajar tranquilos.

### 2. Editar y probar

Hacemos cambios en archivos como:

```text
index.html
styles.css
temario.html
salario.html
apuntes.html
contacto.html
```

Despues abrimos la web en el navegador y revisamos que se vea bien.

### 3. Ver que ha cambiado

```powershell
git status
```

Esto muestra que archivos se han modificado.

### 4. Preparar cambios

Para preparar todo:

```powershell
git add .
```

O solo un archivo:

```powershell
git add styles.css
```

### 5. Guardar en Git local

```powershell
git commit -m "Describe aqui el cambio"
```

Ejemplo:

```powershell
git commit -m "Mejora la navegacion y el diseno movil"
```

### 6. Subir a GitHub

```powershell
git push origin main
```

Cuando esto termina bien, GitHub queda actualizado.

## Que haremos nosotros normalmente

Cuando me pidas cambios, yo trabajare asi:

1. Revisare el estado con `git status`.
2. Editare los archivos necesarios.
3. Probare o revisare lo cambiado.
4. Te dire exactamente que he modificado.
5. Si te gusta, lo guardamos con `git add` y `git commit`.
6. Si quieres publicarlo en GitHub, hacemos `git push`.

La parte importante: no hace falta subir cada prueba a GitHub. Podemos probar en local todo lo que queramos.

## Primer paso para conectar esta carpeta

Cuando quieras conectar esta carpeta al repo, el bloque inicial sera este:

```powershell
git init
git remote add origin https://github.com/Bigdeibeat/opositando-agente-es.git
git fetch origin main
git branch -M main
git status
```

Esto prepara la carpeta local para trabajar con GitHub.

Antes de subir nada, revisaremos que los archivos locales coinciden con los del repo y que no hay sorpresas.

## Resumen rapido

```powershell
git status
```

Ver que ha cambiado.

```powershell
git add .
```

Preparar todos los cambios.

```powershell
git commit -m "Mensaje del cambio"
```

Guardar los cambios en Git local.

```powershell
git push origin main
```

Subir los cambios a GitHub.

```powershell
git pull origin main
```

Traer cambios desde GitHub.

## Regla practica

Si solo estamos probando diseno o textos, trabajamos en local.

Si algo ya esta bien y quieres conservarlo, hacemos commit.

Si quieres que aparezca en GitHub y en el despliegue conectado a GitHub, hacemos push.

