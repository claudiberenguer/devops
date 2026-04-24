# Simple ML Training Project

---

## Trabajo realizado

### 1. Configuración inicial del repositorio

- Creación del repositorio en GitHub para el grupo 5.
- Copia del contenido del repositorio base visto en clase.
- Actualización del `.gitignore`.
- Generación de `requirements.txt` con las librerías necesarias para el proyecto.
- Initial commit con la estructura base revisada del proyecto.

### 2. Pipeline de integración continua (CI)

Se ha creado la carpeta `.github/workflows/` con el fichero `integration.yml`, que define el pipeline de integración continua en GitHub Actions. Los cambios respecto al pipeline original visto en clase son:

- **Versión de Python**: se fija a `3.10` para garantizar compatibilidad.
- **Instalación de dependencias**: se cambia el comando de instalación para usar `pip install -r requirements.txt`.
- **Tolerancia a fallos en tests**: el pipeline se completa aunque los tests fallen, pero notifica el error al final del job.
- **Comentario de resultados en PR**: se corrige el campo `issue_number` usando `context.payload.pull_request.number` para que el comentario con los resultados y la cobertura se publique correctamente en el PR (evitando el fallo que se producía en clase al no identificar el número de PR).

### 3. Validación del pipeline y revisión de PR

- Se abrió una PR con los cambios del `integration.yml` y Sheila actuó como reviewer, aprobándola con el comentario *"looks good to me"*.
- Se validó que el pipeline se ejecuta correctamente de extremo a extremo.

### 4. Despliegue en Render

- Se creó el web service en Render siguiendo el mismo proceso que en clase.
- Al ejecutarlo, se produjo un error relacionado con la carpeta `deployment`, que todavía no existe en el repositorio. Queda pendiente de resolver.

### 5. Ruleset para la rama main

- Se configuró una ruleset en GitHub para proteger la rama `main` con los requisitos indicados en el enunciado.

### 6. Validación del flujo completo con "cambio chorra"

- Se añadió el secreto `RENDER_DEPLOY_HOOK` en GitHub para permitir el despliegue automático desde el pipeline.
- Se realizó un cambio en el `README.md` para verificar que:
  - El pipeline se ejecuta al abrir una PR.
  - La ruleset bloquea el merge hasta que se cumplan los requisitos.
  - Sheila revisó y aprobó la PR, validando el flujo completo.

### 7. Pipeline de build (`build.yml`)

- Se ha configurado el fichero `build.yml` en `.github/workflows/` usando como base el fichero proporcionado por el profesor en Google Drive (carpeta de evaluación).
- Se han aplicado las modificaciones vistas en clase:
  - Descarga del dataset necesario para el entrenamiento.
  - Actualización y publicación del modelo entrenado en la sección de **Releases** de GitHub.
- Se creó una PR con estos cambios. Tras algunos fallos iniciales en el pipeline por equivocación nuestra en el código, Sheila revisó y aprobó la PR, integrando el workflow de build en `main`.

---

## Pendiente

### Por parte de Paris y Claudi

- **Pipeline de deploy**: implementar el workflow de despliegue continuo como indica el enunciado..

### Por parte de todos

- **Simulación de Rollback**: informarse sobre en qué consiste y cómo implementarla en el contexto del proyecto.
- **Revisión del entregable**: verificar conjuntamente que se cumplen todos los requisitos del enunciado antes de la entrega.
