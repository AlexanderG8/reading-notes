# 📋 Read 06: Developer Tools

### 1. ¿Qué hacen los siguientes comandos? 💡  
- `pwd`: 🛤️ Muestra la ruta completa del directorio actual en el que te encuentras.  
- `ls`: 📂 Lista el contenido de un directorio, como archivos y subdirectorios.  
- `cd`: 🚶 Cambia el directorio de trabajo actual.  
- `mkdir`: 🆕 Crea un nuevo directorio.  
- `touch`: ✨ Crea un archivo vacío o actualiza la fecha de modificación de un archivo existente.

---

### 2. ¿Qué sucede en el siguiente escenario si ingresas estos comandos y argumentos? 🧐  
Al ingresar los comandos, primero `cd projects` te lleva al directorio `projects`. Luego, `mkdir new-project` crea un directorio llamado `new-project` dentro de `projects`. Con `touch new-project/newfile.md`, creas un archivo vacío llamado `newfile.md` dentro del directorio `new-project`. Después, con `cd ..`, vuelves al directorio anterior (en este caso, `projects`). Finalmente, al usar `ls projects/new-project`, listará el contenido de `new-project`, mostrando el archivo `newfile.md`.

---

### 3. ¿Qué comando usarías para listar todos los archivos, incluidos los ocultos? 🔍  
Para listar todos los archivos, incluidos los ocultos, en un directorio de Linux o macOS, usarías el comando `ls -a`. 🗂️ El parámetro `-a` significa "all" (todos), lo que incluye archivos que comienzan con un punto (`.`), que son considerados archivos ocultos en Linux y macOS.  

### Fuentes:
- [Comandos esenciales de linux](https://www.hostinger.es/tutoriales/linux-comandos)
- [Linea de comandos](https://ryanstutorials.net/linuxtutorial/commandline.php)
- [Acerca de archivos](https://ryanstutorials.net/linuxtutorial/aboutfiles.php)