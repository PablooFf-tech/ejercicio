# Práctica Git y GitHub

**Alumno:** Pablo Flores  

## Descripción

Repositorio creado para practicar los comandos básicos de Git y GitHub. He trabajado con ramas (`main`, `feature/contacto` y `feature/help-page`), realizado commits y sincronizado los cambios con el repositorio remoto.

### Estructura del proyecto

```text
.
├── README.md
├── assets/
│   └── imagen-github.svg
├── carpeta-1/
│   └── archivo-1.txt
├── carpeta-2/
│   └── archivo-2.txt
├── carpeta-3/
│   └── archivo-3.txt
├── carpeta-4/
│   └── archivo-4.txt
├── contacto/
│   └── contacto.html
└── help/
    └── help.html
```

## Problemas y dudas reales

- **Fetch vs Pull:** Al subir la imagen directamente desde la web de GitHub y ejecutar `git fetch`, vi que la carpeta local no se actualizaba. Entendí que `git fetch` solo descarga la información del remoto, y que para tener el archivo físicamente hace falta usar `git pull`.
- **Merge entre ramas:** Después de hacer `pull` en `main`, la rama `feature/contacto` no tenía la imagen automáticamente. Tuve que cambiar a esa rama con `git switch feature/contacto` y ejecutar `git merge main`.
- **Set-upstream:** Al principio no tenía claro por qué hacía falta `--set-upstream origin main`. Sirve para vincular la rama local con la remota y poder usar simplemente `git push` o `git pull` en los siguientes comandos.

## Historial de la práctica

### Primer commit en main
```text
f87b7fe (HEAD -> main) Crear estructura inicial del proyecto
```

### Commit en feature/contacto
```text
e5c2cad (HEAD -> feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Merge de feature/contacto en main
```text
e5c2cad (HEAD -> main, feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Ampliación opcional (feature/help-page)
```text
942431f (HEAD -> main, feature/help-page) Añadir página de ayuda
e5c2cad (feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Tras subir la imagen en GitHub y actualizar feature/contacto
```text
d5ef0ea (HEAD -> feature/contacto, main) Subir imagen directamente desde GitHub.com
942431f (feature/help-page) Añadir página de ayuda
e5c2cad Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

## Observaciones

- Las ramas sirven para trabajar en funcionalidades nuevas sin modificar la rama principal hasta que todo funcione.
- `git fetch` consulta los cambios del remoto sin modificar los archivos locales, mientras que `git pull` los descarga e integra.
- `git merge` combina los cambios de una rama en otra.

## Respuestas a las preguntas

1. **Diferencia entre local y remoto:** El local está en mi ordenador y el remoto en GitHub.
2. **`git clone`:** Descarga una copia de un repositorio remoto a mi PC.
3. **`git remote -v`:** Muestra las URLs de GitHub conectadas al repositorio local.
4. **Diferencia entre `add`, `commit` y `push`:** `add` prepara los cambios, `commit` los guarda localmente y `push` los sube a GitHub.
5. **`--set-upstream`:** Vincula la rama local con la remota para no tener que escribir el nombre de la rama en cada `push` o `pull`.
6. **Diferencia entre `push` y `pull`:** `push` sube cambios al remoto y `pull` los descarga al PC.
7. **`git fetch`:** Descarga la información del remoto sin modificar los archivos de la carpeta local.
8. **Por qué la imagen no aparece tras `git fetch`:** Porque `fetch` solo actualiza el historial interno; hace falta un `pull` o `merge` para actualizar los archivos reales.
9. **`git merge`:** Une el historial y los cambios de una rama dentro de otra.
10. **Diferencia entre `main` y `feature/contacto`:** `main` es la rama principal con el código estable y `feature/contacto` era la rama donde desarrollé la sección de contacto.
11. **Qué ocurre con los commits al hacer merge:** Se integran en el historial de la rama destino.
12. **Cambios en GitHub no conocidos por el local:** El remoto se queda por delante del local. Hay que hacer `git pull` antes de poder hacer `push`.
13. **`git log --oneline`:** Muestra el historial de commits resumido en una línea por commit.
