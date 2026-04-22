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