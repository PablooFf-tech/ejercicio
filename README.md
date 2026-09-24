# Práctica: Git, ramas y trabajo con GitHub

**Alumno:** Pablo Flores  
**Fecha:** Septiembre 2026  

---

## Descripción

En esta práctica he trabajado con un repositorio local de Git y lo he sincronizado con mi cuenta de GitHub. El objetivo ha sido aprender a manejar ramas (`main`, `feature/contacto` y la ampliación `feature/help-page`), hacer commits organizados, sincronizar cambios entre mi ordenador y el remoto (`push`, `fetch`, `pull`) y entender cómo resolver las diferencias cuando se suben archivos directamente desde GitHub.

### Estructura final del proyecto

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

---

## Problemas y dudas

Durante el desarrollo de la práctica me surgieron algunas dudas reales sobre cómo funciona Git:

1. **Diferencia entre `git fetch` y `git pull`:**
   - **Lo que ocurrió:** Al subir una imagen desde la web de GitHub y ejecutar `git fetch` en mi terminal, vi que en el estado del repositorio se detectaba el cambio remoto, pero el archivo no aparecía físicamente en mi carpeta.
   - **Explicación:** Descubrí que `git fetch` solo descarga la información del remoto para que Git local sepa lo que hay nuevo, pero no toca los archivos de mi carpeta de trabajo. Para traer los archivos físicamente tuve que ejecutar `git pull`.

2. **Actualizar ramas secundarias:**
   - **Lo que ocurrió:** Tras hacer el `pull` en `main` y traer la imagen de GitHub, cambié a la rama `feature/contacto` y vi que la imagen no estaba ahí.
   - **Explicación:** Las ramas son independientes. Para tener los cambios de `main` en `feature/contacto`, tuve que ponerme en la rama de contacto (`git switch feature/contacto`) y hacer un `git merge main`.

3. **Uso de `--set-upstream`:**
   - **Duda:** ¿Por qué la primera vez hay que poner `--set-upstream origin <rama>`?
   - **Explicación:** Sirve para enlazar la rama local con la rama de GitHub. Así, a partir de ese momento solo hace falta poner `git push` o `git pull` a secas.

---

## Historial de la práctica (`git log --oneline`)

### 1. Historial tras el primer commit en la rama principal (`main`)
```text
f87b7fe (HEAD -> main) Crear estructura inicial del proyecto
```

### 2. Historial en la rama `feature/contacto`
```text
e5c2cad (HEAD -> feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### 3. Historial tras hacer merge de `feature/contacto` en `main`
```text
e5c2cad (HEAD -> main, feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### 4. Historial tras la ampliación opcional (`feature/help-page`)
```text
942431f (HEAD -> main, feature/help-page) Añadir página de ayuda
e5c2cad (feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### 5. Historial tras traer los cambios de GitHub y actualizar `feature/contacto`
```text
d5ef0ea (HEAD -> feature/contacto, main) Subir imagen directamente desde GitHub.com
942431f (feature/help-page) Añadir página de ayuda
e5c2cad Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

---

## Observaciones

- **Ramas:** Me han permitido trabajar en nuevas secciones (como la página de contacto o la de ayuda) en un sitio separado sin tocar el código de la rama principal hasta que estaba listo.
- **Commits:** Son como puntos de guardado donde dejamos constancia de qué hemos cambiado y por qué.
- **Merge:** Sirve para juntar el trabajo de dos ramas. En estos casos ha unido los commits sin problemas.
- **Diferencia entre Push, Fetch y Pull:**
  - `git push`: Sube lo que he hecho en mi PC a GitHub.
  - `git fetch`: Comprueba qué hay de nuevo en GitHub pero sin tocar mis archivos locales.
  - `git pull`: Descarga las novedades de GitHub y las mezcla en mi carpeta de trabajo.

---

## Respuestas a las preguntas de la práctica

### 1. ¿Qué diferencia hay entre el repositorio local y el remoto?
El repositorio local está guardado en mi propio ordenador (puedo trabajar sin internet). El remoto está alojado en GitHub en la nube y sirve para guardar una copia de respaldo y compartir el código con otras personas.

### 2. ¿Qué hace `git clone`?
Descarga una copia completa de un repositorio de GitHub a nuestro ordenador y lo deja listo para empezar a trabajar con Git.

### 3. ¿Para qué sirve `git remote -v`?
Muestra a qué repositorio remoto (URL de GitHub) está conectado nuestro proyecto local tanto para subir (`push`) como para descargar (`fetch`) datos.

### 4. ¿Qué diferencia hay entre `git add`, `git commit` y `git push`?
- `git add`: Prepara los archivos modificados que queremos incluir en el siguiente guardado.
- `git commit`: Guarda esos cambios en el historial de Git en nuestro ordenador con un mensaje explicativo.
- `git push`: Sube esos commits guardados en local al repositorio de GitHub.

### 5. ¿Qué hace `--set-upstream`?
Conecta la rama de nuestro ordenador con la rama correspondiente en GitHub para que luego podamos usar `git push` y `git pull` directamente sin escribir el nombre de la rama cada vez.

### 6. ¿Qué diferencia hay entre `git push` y `git pull`?
`git push` envía los cambios de nuestro PC a GitHub (subir), mientras que `git pull` trae e integra los cambios de GitHub a nuestro PC (descargar).

### 7. ¿Qué hace `git fetch`?
Descarga los datos e información nueva que hay en GitHub, pero sin modificar nuestros archivos de trabajo.

### 8. ¿Por qué después de `git fetch` puede que la imagen todavía no aparezca en nuestra carpeta?
Porque `git fetch` solo actualiza el registro interno de Git sobre lo que hay en el remoto. Para que el archivo aparezca físicamente en la carpeta hay que hacer un `git pull` o `git merge`.

### 9. ¿Qué hace `git merge`?
Junta los cambios y el historial de una rama dentro de otra rama (por ejemplo, juntar `feature/contacto` dentro de `main`).

### 10. ¿Qué diferencia hay entre la rama principal y `feature/contacto`?
La rama principal (`main`) contiene el proyecto base y estable, mientras que `feature/contacto` era la rama de trabajo aislada donde estuve creando la página de contacto.

### 11. ¿Qué ocurre con los commits cuando hacemos un merge?
Los commits que habíamos hecho en la rama secundaria pasan a formar parte del historial de la rama principal.

### 12. ¿Qué ocurre cuando modificamos el repositorio desde GitHub y nuestro ordenador todavía no conoce ese cambio?
El repositorio remoto se queda un paso por delante de nuestro ordenador. Si intentamos hacer `git push`, Git nos dará un error avisando de que primero debemos hacer `git pull` para estar actualizados.

### 13. ¿Para qué sirve `git log --oneline`?
Muestra el historial de commits de forma resumida (cada commit en una sola línea con su identificador y su mensaje).
