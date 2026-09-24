# Práctica Git y GitHub - Flujo de Trabajo con Ramas

Proyecto para la práctica de control de versiones con Git y repositorio remoto en GitHub.

## Descripción del Proyecto

Este repositorio demuestra el uso práctico de comandos fundamentales de Git y flujos de trabajo colaborativos en GitHub:
- Creación y clonación de repositorios.
- Gestión de ramas (`main`, `feature/contacto`, `feature/help-page`).
- Creación y registro de commits ordenados.
- Sincronización remota (`git push`, `git fetch`, `git pull`).
- Fusión de ramas (`git merge`) y resolución de diferencias entre entornos local y remoto.

---

## Estructura del Proyecto

```text
.
├── README.md
├── carpeta-1/
│   └── archivo-1.txt
├── carpeta-2/
│   └── archivo-2.txt
├── carpeta-3/
│   └── archivo-3.txt
└── carpeta-4/
    └── archivo-4.txt
```

---

## Problemas y dudas

Durante el desarrollo de esta práctica han surgido las siguientes observaciones y cuestiones técnicas reales:

1. **Diferencia entre `git fetch` y `git pull`:**
   - **Duda/Problema:** Al subir una imagen directamente en GitHub y ejecutar `git fetch` en local, la imagen no aparecía físicamente en el directorio del ordenador aunque `git status` detectaba cambios en la rama remota.
   - **Solución:** `git fetch` únicamente actualiza las referencias remotas (`origin/main`) en la base de datos de Git local. Para aplicar e integrar los cambios en el árbol de trabajo (los archivos locales), es necesario ejecutar `git pull` (o `git merge origin/main`).

2. **Sincronización de ramas secundarias tras cambios en el remoto:**
   - **Duda/Problema:** Tras hacer `git pull` en `main` para traer la imagen subida desde GitHub, la rama `feature/contacto` no contenía dicha imagen.
   - **Solución:** Las ramas en Git son independientes. Para incorporar los cambios de `main` en `feature/contacto`, se debe hacer `git switch feature/contacto` y posteriormente `git merge main`.

3. **Uso del parámetro `--set-upstream` (`-u`):**
   - **Duda/Problema:** ¿Por qué la primera vez que subimos una rama nueva hay que especificar `git push --set-upstream origin <nombre-rama>`?
   - **Explicación:** Establece la vinculación (tracking) entre la rama local y la remota. En subidas y descargas posteriores basta con ejecutar `git push` o `git pull`.

---

## Historial de la práctica

*(Se irá actualizando secuencialmente según cada fase del ejercicio)*
