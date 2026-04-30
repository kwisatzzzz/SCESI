# Apuntes de Clase: SCESI
**Estudiante:** Camila Magne Hinojosa

---

## Dia 1: Introduccion a Git y Configuracion Inicial
*Fecha: 20 de abril de 2026*

### Que es Git?
[cite_start]Git es un Sistema de Control de Versiones Distribuido (VCS)[cite: 3, 4]. 
[cite_start]Permite guardar archivos y gestionar sus versiones a lo largo del tiempo de manera local[cite: 5, 6, 7].

### Historia de Git
* [cite_start]Nacio tras un conflicto con la herramienta BitKeeper[cite: 13, 14].
* [cite_start]Linus Torvalds decidio desarrollarlo el mismo[cite: 17, 18].
* [cite_start]Fue creado en un periodo de aproximadamente 2 a 3 semanas[cite: 20].

### Instalacion y Verificacion
[cite_start]Para instalar Git, se debe acudir a la pagina oficial: `https://git-scm.com/install/`[cite: 22].
[cite_start]Para verificar que la instalacion fue exitosa, se usa el comando[cite: 23]:
`git --version`

### Configuraciones Globales
[cite_start]Es fundamental configurar el usuario antes de empezar a trabajar[cite: 24]:

```bash
git config --global user.name "Camila Magne Hinojosa"
git config --global user.email "tu@correo.com"
git config --global core.autocrlf true

---

## Dia 2: Estados de Git y Buenas Practicas de Commits
*Fecha: 22 de abril de 2026*

### Estados de Git
Git gestiona los archivos a traves de tres estados principales:
1. **Directorio de Trabajo (Modified):** Es la carpeta local donde se escribe codigo que Git aun no tiene asegurado. Los archivos pueden estar como *Untracked* (nuevos) o *Modified* (cambiados).
2. **Stage Area (Staged):** Es el area de preparacion donde se seleccionan los cambios que se incluiran en el siguiente punto de guardado.
3. **Repositorio Local (Committed):** Es el historial donde los cambios ya tienen un ID (hash) y estan confirmados.

### Comandos de Gestion de Estados
* `git add <archivo>`: Agrega un archivo especifico al stage area.
* `git add .`: Agrega todos los archivos observados al stage area.
* `git restore <archivo>`: Revierte un archivo modificado a su estado original (borra cambios fisicos).
* `git restore --staged <archivo>`: Saca un archivo del stage area para volver al estado anterior.
* `git reset --soft HEAD~1`: Deshace el ultimo commit realizado.

### Buenas Practicas de Commits
* **Commits Atomicos:** Realizar confirmaciones pequeñas que representen un unico cambio logico y completo.
* **Mensajes Imperativos:** Los mensajes deben describir que hace el commit usando verbos como Add, Change, Fix o Remove.
* **Formato Semantico:** Se debe usar el formato `<tipo>: <descripcion>` (ej. `feat`, `fix`, `docs`).
* **Restricciones:** No usar punto final ni puntos suspensivos, y mantener el titulo bajo los 50 caracteres para mayor concision.

---

## Dia 3: GitHub y Conexion Segura (SSH)
*Fecha: 23 de abril de 2026*

### Git vs GitHub
Es importante entender que no son lo mismo:
* **Git:** Es el sistema de control de versiones que gestiona los archivos localmente en la computadora.
* **GitHub:** Es una plataforma en la nube que permite alojar repositorios de Git para colaborar y compartir el codigo.

### Metodos de Conexion: SSH vs HTTPS
* **HTTPS:** Es el metodo por defecto, pero requiere autenticacion constante mediante tokens o contraseñas, lo cual puede ser tedioso.
* **SSH:** Permite una comunicacion segura entre la computadora y GitHub mediante una llave (SSH Key). Una vez configurada, no solicita credenciales en cada operacion.

### Comandos de Sincronizacion Remota
* `git remote add origin <URL>`: Vincula el repositorio local con un servidor remoto.
* `git push origin <rama>`: Envia los commits locales al repositorio en la nube.
* `git pull origin <rama>`: Descarga y fusiona los cambios del servidor a la computadora local.
* `git clone <URL>`: Crea una copia local de un repositorio que ya existe en GitHub.
* `git remote set-url origin <URL>`: Permite cambiar la direccion del repositorio remoto (ej. pasar de HTTPS a SSH).
---

## Dia 4: Remotos, Multiples SSH y Git Checkout

### Gestion de Remotos
El comando `git remote` permite administrar las conexiones con repositorios externos, indicando a Git local donde enviar o traer informacion.
* `git remote -v`: Permite ver las URLs exactas a las que apunta el repositorio.
* `git remote add <apodo> "url"`: Vincula el repositorio local con uno en la nube.
* `git remote set-url <apodo> "url"`: Cambia la direccion a la que apunta el repositorio.

### Multiples SSH y Jerarquia de Configuracion
Para manejar multiples cuentas en GitHub, es util tener mas de una llave SSH para que estas no choquen. Se debe crear un archivo `config` para asignar un Host distinto a cada llave, definiendo el `HostName`, `User` y la ruta exacta en `IdentityFile`. 
Ademas, Git maneja una jerarquia de configuracion: **System > Global > Local**. Las configuraciones locales se imponen a las globales y se aplican usando `git config` sin la bandera `--global`.

### Git Checkout y Detached HEAD
`git checkout` es un comando que permite desplazar el HEAD hacia un punto especifico de la historia o a una rama distinta para inspeccionar, restaurar o experimentar.
* **Detached HEAD:** Ocurre cuando el HEAD apunta directamente a un commit (que es fijo) en lugar de a una rama. En este estado, eres un espectador en el pasado. 
* Si realizas cambios sin crear una nueva rama y vuelves al presente, tus cambios desapareceran en el vacio. Como buena practica, limpia tu directorio de trabajo antes de hacer checkout al pasado.

---

## Dia 5: Ramas y Gitflow Basico

### Ramas (Branches) en Git
Las ramas son una bifurcacion del estado del codigo que crea un nuevo camino evolutivo en paralelo.
* `git branch`: Lista las ramas disponibles y muestra el posicionamiento actual del HEAD.
* `git branch <rama>`: Crea una nueva rama a partir de la rama posicionada.
* `git branch -D <rama>`: Borra la rama especificada.

### Git Checkout vs Git Switch
Originalmente, `git checkout` estaba sobrecargado, ya que servia para cambiar ramas, viajar a commits antiguos y restaurar archivos. Para evitar dejar el proyecto en *Detached HEAD* accidentalmente, se introdujo `git switch` en 2019, un comando especializado unicamente en la navegacion segura de ramas.

### Gitflow Basico
Es un flujo de trabajo que nos permite gestionar las ramas de manera ordenada mediante ciertas reglas.
* **Ramas Principales:**
  * `main`: Contiene el codigo oficial que se encuentra en produccion.
  * `develop`: Rama de pre-produccion donde se integran y prueban las nuevas caracteristicas.
* **Ramas de Apoyo:**
  * `feature/*`: Para desarrollar una tarea especifica o nueva caracteristica. Nacen en `develop` y mueren en `develop`.
  * `release/*`: Para preparar y pulir el lanzamiento de una nueva version (pruebas QA). Nacen en `develop` y mueren en `main` y `develop`.
  * `hotfix/*`: Para arreglar parches o incendios de emergencia en produccion. Nacen en `main` y mueren en `main` y `develop`.

  ---

## Dia 6: Fusion de Ramas y Flujo Colaborativo

### Comandos de Sincronizacion y Fusion
* `git fetch`: Verifica de forma segura si existen nuevos cambios en el repositorio remoto sin modificar tus archivos locales.
* `git pull origin <rama>`: Descarga e integra todos los cambios del repositorio remoto hacia tu rama local.
* `git push origin <rama>`: Sube tus commits locales al repositorio remoto. 
  * *Nota:* La primera vez que se sube una rama nueva, se debe usar la bandera `-u` (`git push -u origin <rama>`) para vincularla y evitar problemas de permisos.
* `git merge <rama>`: Permite fusionar dos ramas en una sola, combinando sus commits. 
  * **Flag `--no-ff` (No Fast-Forward):** Fuerza la creacion de un commit de fusion. Esto asegura que no se pierda el historial visual de la rama integrada, incluso si esta se elimina despues.

### Flujo de Trabajo Colaborativo (Paso a Paso)
Para trabajar en equipo de manera ordenada, previniendo la perdida de codigo:

1. **Actualizar la base (develop):**
   `git checkout develop`
   `git fetch`
   `git pull origin develop`
2. **Crear rama propia e integrar novedades:**
   `git checkout -b <tu_rama>`
   `git merge develop` *(Solo si hubo cambios en develop)*
3. **Trabajar y subir avances:**
   *(Realizar cambios, git add y git commit)*
   `git push -u origin <tu_rama>`
4. **Integracion final:**
   `git checkout develop`
   `git fetch`
   `git pull origin develop`
   `git merge --no-ff <tu_rama>`
5. **Resolucion y limpieza:**
   *(Si hay conflictos: resolver manualmente, git add y git commit)*
   `git branch -D <tu_rama>`
   `git push origin develop`