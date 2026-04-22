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