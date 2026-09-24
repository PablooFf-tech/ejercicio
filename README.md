# Práctica Git, Ramas y Trabajo con GitHub

**Autor:** Pablo Flores  
**Perfil:** Desarrollador Full-Stack / Web (en formación)  
**Fecha:** Septiembre 2026  

---

## 1. Descripción del Proyecto

Este proyecto es una práctica completa del flujo de trabajo profesional con Git y GitHub. En él se demuestra el control de versiones local, la creación y fusión de ramas de características (`feature/contacto`, `feature/help-page`), el envío de cambios al entorno remoto, y la resolución de divergencias al recibir actualizaciones realizadas directamente en GitHub.com.

### Estructura final del repositorio:

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

## 2. Problemas y Dudas Reales

Durante la realización de la práctica se han identificado los siguientes aspectos técnicos clave:

1. **Diferencia entre `git fetch` y `git pull`:**
   - **Observación:** Tras añadir un archivo directamente desde la interfaz web de GitHub y ejecutar `git fetch` localmente, el nuevo archivo no aparecía en el directorio de trabajo del ordenador.
   - **Explicación:** `git fetch` descarga la información y los objetos del repositorio remoto a la base de datos local de Git (actualizando la referencia `origin/main`), pero **no modifica** la rama de trabajo actual ni sus archivos. Para integrar visual y físicamente los cambios en la carpeta de trabajo se requiere `git pull` (o `git merge origin/main`).

2. **Propagación de cambios entre ramas independientes:**
   - **Observación:** Al actualizar la rama principal `main` con los cambios del remoto, la rama `feature/contacto` no contenía automáticamente la nueva imagen.
   - **Explicación:** Cada rama en Git es una línea de tiempo independiente. Para llevar las novedades de `main` a `feature/contacto` fue necesario cambiar a dicha rama (`git switch feature/contacto`) y ejecutar el merge explícito (`git merge main`).

3. **Vinculación de ramas con `--set-upstream` (`-u`):**
   - **Observación:** La primera vez que se publica una rama local en GitHub, es imprescindible indicar `--set-upstream origin <rama>`.
   - **Explicación:** Este comando crea la relación de seguimiento (tracking branch). A partir de ese momento, Git sabe qué rama remota se corresponde con la rama local actual, permitiendo usar simplemente `git push` o `git pull` sin argumentos adicionales.

---

## 3. Historial de la Práctica (`git log --oneline`)

### Fase 1: Estructura inicial en la rama principal (`main`)
```bash
$ git log --oneline
f87b7fe (HEAD -> main) Crear estructura inicial del proyecto
```

### Fase 2: Desarrollo en la rama `feature/contacto`
```bash
$ git log --oneline
e5c2cad (HEAD -> feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Fase 3: Fusión de `feature/contacto` en la rama principal (`main`)
```bash
$ git log --oneline
e5c2cad (HEAD -> main, feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Fase 4: Ampliación opcional — Desarrollo y fusión de `feature/help-page`
```bash
$ git log --oneline
942431f (HEAD -> main, feature/help-page) Añadir página de ayuda
e5c2cad (feature/contacto) Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

### Fase 5: Actualización desde el remoto (GitHub) e integración en `feature/contacto`
```bash
$ git log --oneline
d5ef0ea (HEAD -> feature/contacto, main) Subir imagen directamente desde GitHub.com
942431f (feature/help-page) Añadir página de ayuda
e5c2cad Añadir página de contacto
f87b7fe Crear estructura inicial del proyecto
```

---

## 4. Observaciones Técnicas

- **Trabajo con Ramas (`git branch`, `git switch`):** Las ramas permiten desarrollar funcionalidades de manera aisada sin alterar el código estable de la rama principal (`main`).
- **Commits:** Representan fotogramas (snapshots) de los cambios preparados en el área de ensayo (*staging*).
- **Fusión (`git merge`):** Une historiales de distintas ramas. En este proyecto se realizaron fusiones *Fast-Forward* donde el puntero de la rama destino avanzó linealmente hasta el commit más reciente de la rama origen.
- **Flujo Remoto (`push`, `fetch`, `pull`):**
  - `git push`: Envía los commits locales al repositorio remoto en GitHub.
  - `git fetch`: Consulta y descarga las novedades del remoto sin tocar la carpeta local.
  - `git pull`: Ejecuta un `fetch` seguido de un `merge` directo en la rama local.

---

## 5. Preguntas y Respuestas Teorico-Prácticas

### 1. ¿Qué diferencia hay entre el repositorio local y el remoto?
- **Local (PC):** Es la copia del repositorio que reside en el disco duro del ordenador. Permite trabajar sin conexión a internet, crear ramas, editar archivos y realizar commits.
- **Remoto (GitHub):** Es el repositorio alojado en los servidores de GitHub en la nube. Sirve como punto centralizado de respaldo, sincronización e integración del código para trabajo colaborativo.

### 2. ¿Qué hace `git clone`?
Descarga una copia completa de un repositorio remoto de GitHub a tu equipo local. Crea el directorio del proyecto, inicializa Git automáticamente y configura la conexión remota llamada `origin`.

### 3. ¿Para qué sirve `git remote -v`?
Muestra las URLs de los repositorios remotos vinculados al proyecto local, detallando las direcciones configuradas para lectura (`fetch`) y escritura (`push`).

### 4. ¿Qué diferencia hay entre `git add`, `git commit` y `git push`?
- `git add`: Mueve las modificaciones del área de trabajo al área de ensayo (*Staging Area*), seleccionando qué cambios formarán parte del próximo commit.
- `git commit`: Guarda de forma permanente las modificaciones preparadas en la base de datos local de Git con un mensaje descriptivo.
- `git push`: Sube los commits guardados localmente al repositorio remoto en GitHub.

### 5. ¿Qué hace `--set-upstream`?
Configura una relación de rastreo (*tracking*) entre la rama local actual y su rama correspondiente en el remoto (`origin`). Permite que en comandos posteriores solo tengamos que escribir `git push` o `git pull`.

### 6. ¿Qué diferencia hay entre `git push` y `git pull`?
- `git push`: Envía la información **desde el local hacia el remoto** (subida).
- `git pull`: Trae e integra la información **desde el remoto hacia el local** (descarga + merge).

### 7. ¿Qué hace `git fetch`?
Descarga las novedades, ramas y referencias enviadas al repositorio remoto desde la última sincronización, **sin aplicar ni fusionar** ningún cambio en los archivos de tu carpeta de trabajo.

### 8. ¿Por qué después de `git fetch` puede que la imagen todavía no aparezca en nuestra carpeta?
Porque `git fetch` solo actualiza el historial y punteros internos de Git (`origin/main`). No modifica los archivos físicos de tu directorio activo hasta que ejecutes un `git merge` o `git pull`.

### 9. ¿Qué hace `git merge`?
Combina el historial de commits y los cambios de una rama origen dentro de la rama actual en la que te encuentras posicionado.

### 10. ¿Qué diferencia hay entre la rama principal y `feature/contacto`?
La rama principal (`main`) contiene el código estable de producción del proyecto. La rama `feature/contacto` es un entorno aislado donde se desarrolló específicamente la sección de contacto sin riesgo de romper la rama principal.

### 11. ¿Qué ocurre con los commits cuando hacemos un merge?
Los commits realizados en la rama de características se incorporan al historial de la rama destino. En fusiones *fast-forward*, el puntero de la rama simplemente avanza; en fusiones con divergencia, se genera un commit de merge (*merge commit*) que une ambas ramas.

### 12. ¿Qué ocurre cuando modificamos el repositorio desde GitHub y nuestro ordenador todavía no conoce ese cambio?
Se produce una desincronización en la que el repositorio remoto está por delante del local. Si intentamos hacer `git push` sin haber hecho previamente `git pull`, Git rechazará el push exigiendo actualizar la rama local primero.

### 13. ¿Para qué sirve `git log --oneline`?
Muestra el historial de commits de forma compacta y resumida en una sola línea por commit, mostrando el hash abreviado y el mensaje del commit.
