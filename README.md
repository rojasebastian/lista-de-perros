# 🐶 Lista de perros

Aplicación web simple que muestra imágenes de perros aleatorias (obtenidas desde la API pública [dog.ceo](https://dog.ceo/dog-api/)) y permite marcarlas como "me gusta" o "no me gusta".

Este repositorio corresponde a la **Evaluación Parcial N°1** de la asignatura **Ingeniería DevOps (DOY0101)**: preparar la base de trabajo (repositorio, ramas, convenciones y automatización) para el pipeline DevOps que se construirá durante el semestre.

---

## 🚀 Cómo levantar el proyecto localmente

No requiere instalación de dependencias. Basta con abrir `index.html` en el navegador, o servirlo con un servidor estático simple:

```bash
npx serve .
```

---

## 🌳 Estrategia de ramificación

Este proyecto utiliza **GitFlow** como modelo de ramificación, con las siguientes ramas:

| Rama | Propósito |
|---|---|
| `main` | Código estable, listo para producción. |
| `develop` | Rama de integración donde convergen los `feature/*` antes de pasar a `main`. |
| `feature/<nombre>` | Nuevas funcionalidades, creadas desde `develop` y fusionadas de vuelta a `develop`. |
| `hotfix/<nombre>` | Correcciones urgentes sobre producción, creadas desde `main` y fusionadas a `main` **y** a `develop`. |

> ✏️ **Pendiente por completar por el equipo:** la pauta pide que la elección quede **justificada** considerando el tamaño del proyecto, la frecuencia de cambios esperada y el tamaño del equipo (2 personas). Como referencia rápida para redactar esa justificación en sus propias palabras:
>
> - **GitFlow** ordena bien el trabajo cuando hay releases diferenciados entre "en desarrollo" y "en producción", aunque agrega más ramas y pasos que un equipo de 2 personas podría no necesitar siempre.
> - **Trunk-based development** es más liviano (casi todo el trabajo va directo a una rama principal con ramas de vida corta), y suele preferirse en equipos pequeños con integración muy frecuente.
>
> Reemplacen este bloque por su propia justificación técnica (no puede ser redactada por IA, según las indicaciones de la evaluación).

---

## 📝 Convenciones de commits

Se utiliza el formato de **Conventional Commits**:

```
<tipo>: <descripción breve en modo imperativo>
```

| Tipo | Uso |
|---|---|
| `feat` | Nueva funcionalidad |
| `fix` | Corrección de errores |
| `docs` | Cambios solo en documentación |
| `style` | Cambios de formato que no afectan la lógica (espacios, indentación) |
| `refactor` | Cambios internos que no agregan funcionalidad ni corrigen errores |
| `chore` | Tareas de mantenimiento (configuración, dependencias, CI) |

Ejemplos usados en este repositorio: `feat: agrega contador de likes y dislikes visible en pantalla`, `fix: corrige spinner que no desaparece cuando la API repite una imagen`.

---

## 🔀 Convenciones de naming de ramas

- `feature/<nombre-descriptivo>` → nuevas funcionalidades. Ej: `feature/contador-likes`.
- `hotfix/<nombre-descriptivo>` → correcciones urgentes sobre `main`. Ej: `hotfix/fix-imagen-repetida`.
- Nombres en **minúsculas**, separados por guiones, y lo suficientemente descriptivos para entender el cambio sin abrir el código.

---

## 🔍 Estrategia de revisión (Pull Requests)

Todo cambio se integra mediante Pull Request, nunca con push directo a `main` o `develop`:

- PR de `feature/*` → `develop`.
- PR de `hotfix/*` → `main` **y** posteriormente hacia `develop` (para no perder la corrección).
- Antes de aprobar un PR debe cumplirse:
  1. El check de GitHub Actions (`CI - Validación básica`) debe pasar en verde.
  2. Al menos un/a integrante del equipo (distinto de quien abrió el PR) debe revisar y aprobar los cambios.
  3. La descripción del PR debe explicar qué cambia y por qué.

> ✏️ **Pendiente:** documenten aquí cualquier criterio adicional que hayan usado realmente al revisar sus PRs (ej. capturas, pruebas manuales realizadas, etc.).

---

## ⚙️ Automatización (CI/CD)

Se configuró un workflow de **GitHub Actions** (`.github/workflows/ci.yml`) que se ejecuta:

- En cada **push a `develop`**: valida automáticamente la sintaxis de `index.js`, la estructura de `index.html` (HTMLHint) y los estilos de `style.css` (Stylelint).
- En cada **Pull Request hacia `main`**: ejecuta la misma validación como control de calidad antes de integrar a producción.

Esto simula, a pequeña escala, el rol que cumple la integración continua (CI) en un pipeline DevOps real: detectar errores automáticamente antes de que lleguen a producción, sin depender de una revisión manual exhaustiva.

---

## 📁 Estructura de carpetas

```
Lista-de-perros/
├── .github/
│   └── workflows/
│       └── ci.yml
├── index.html
├── index.js
├── style.css
├── .gitignore
└── README.md
```

---

## 🔧 Cambios simulados en este ciclo de desarrollo

| Rama | Tipo | Descripción |
|---|---|---|
| `feature/contador-likes` | feature | Agrega un contador visible de likes/dislikes en pantalla. |
| `feature/modo-oscuro` | feature | Agrega un botón para alternar entre modo claro y modo oscuro. |
| `hotfix/fix-imagen-repetida` | hotfix | Corrige un bug en el que, si la API entregaba dos veces seguidas la misma imagen, el spinner de carga quedaba visible para siempre (el evento `load` no se vuelve a disparar si el `src` no cambia). |

---

## 👥 Autores

- Integrante 1 — nombre
- Integrante 2 — nombre

---

## 🤖 Uso de Inteligencia Artificial

> ✏️ **Obligatorio completar según la política de la evaluación:** declaren aquí qué herramienta de IA usaron, para qué (ej. redacción de documentación, generación del workflow de GitHub Actions, plantillas), y confirmen que las justificaciones técnicas y reflexiones individuales fueron redactadas por el equipo. Referencia: https://bibliotecas.duoc.cl/ia

## 🧠 Reflexiones individuales

> ✏️ **Obligatorio, sin apoyo de IA.** Cada integrante debe agregar aquí su propia reflexión sobre su aprendizaje y su contribución al proyecto.

- **Integrante 1:** _(pendiente)_
- **Integrante 2:** _(pendiente)_

*Proyecto original: repaso de conexión a API y manejo de eventos en JavaScript. Adaptado como base para la Evaluación Parcial N°1, DOY0101 — Ingeniería DevOps.*
