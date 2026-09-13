# 🐶 Lista de perros

Aplicación web simple que muestra imágenes de perros aleatorias (obtenidas desde la API pública [dog.ceo](https://dog.ceo/dog-api/)) y permite marcarlas como "me gusta" o "no me gusta".

Este repositorio corresponde a la *Evaluación Parcial N°1* de la asignatura *Ingeniería DevOps (DOY0101)*: preparar la base de trabajo (repositorio, ramas, convenciones y automatización) para el pipeline DevOps que se construirá durante el semestre.

---

## 🚀 Cómo levantar el proyecto localmente

No requiere instalación de dependencias. Basta con abrir index.html en el navegador, o servirlo con un servidor estático simple:

bash
npx serve .


---

## 🌳 Estrategia de ramificación

Este proyecto utiliza *GitFlow* como modelo de ramificación, con las siguientes ramas:

| Rama | Propósito |
|---|---|
| main | Código estable, listo para producción. |
| develop | Rama de integración donde convergen los feature/* antes de pasar a main. |
| feature/<nombre> | Nuevas funcionalidades, creadas desde develop y fusionadas de vuelta a develop. |
| hotfix/<nombre> | Correcciones urgentes sobre producción, creadas desde main y fusionadas a main *y* a develop. |

> Nuestro equipo optó por *GitFlow* como estrategia de ramificación. Durante las tres semanas de desarrollo, los cambios se integraron de forma esporádica, concentrando gran parte del trabajo en bloques puntuales y dejando la revisión y corrección de errores para el final del proceso.
>
> - Dado que el código del proyecto es acotado, los errores resultaban fáciles de detectar y corregir rápidamente, por lo que en la práctica no sentimos una necesidad real de mantener main como una rama protegida y separada del resto del trabajo: nos habría dado lo mismo desarrollar todo sobre una única rama principal.
> - Aun así, decidimos mantener los pasos adicionales de GitFlow (develop, feature/* y hotfix/*) porque, incluso siendo un equipo de solo dos personas, no los sentimos como una carga extra de trabajo, sino como pasos casi necesarios para que el desarrollo quedara bien ordenado y documentado.
>
> 

---

## 📝 Convenciones de commits

Se utiliza el formato de *Conventional Commits*:


<tipo>: <descripción breve en modo imperativo>


| Tipo | Uso |
|---|---|
| feat | Nueva funcionalidad |
| fix | Corrección de errores |
| docs | Cambios solo en documentación |
| style | Cambios de formato que no afectan la lógica (espacios, indentación) |
| refactor | Cambios internos que no agregan funcionalidad ni corrigen errores |
| chore | Tareas de mantenimiento (configuración, dependencias, CI) |

Ejemplos usados en este repositorio: feat: agrega contador de likes y dislikes visible en pantalla, fix: corrige spinner que no desaparece cuando la API repite una imagen.

---

## 🔀 Convenciones de naming de ramas

- feature/<nombre-descriptivo> → nuevas funcionalidades. Ej: feature/contador-likes.
- hotfix/<nombre-descriptivo> → correcciones urgentes sobre main. Ej: hotfix/fix-imagen-repetida.
- Nombres en *minúsculas*, separados por guiones, y lo suficientemente descriptivos para entender el cambio sin abrir el código.

---

## 🔍 Estrategia de revisión (Pull Requests)

Todo cambio se integra mediante Pull Request, nunca con push directo a main o develop:

- PR de feature/* → develop.
- PR de hotfix/* → main **y** posteriormente hacia develop (para no perder la corrección).
- Antes de aprobar un PR debe cumplirse:
  1. El check de GitHub Actions (CI - Validación básica) debe pasar en verde.
  2. Al menos un/a integrante del equipo (distinto de quien abrió el PR) debe revisar y aprobar los cambios.
  3. La descripción del PR debe explicar qué cambia y por qué.

> 
---

## ⚙️ Automatización (CI/CD)

Se configuró un workflow de *GitHub Actions* (.github/workflows/ci.yml) que se ejecuta:

- En cada *push a develop*: valida automáticamente la sintaxis de index.js, la estructura de index.html (HTMLHint) y los estilos de style.css (Stylelint).
- En cada *Pull Request hacia main*: ejecuta la misma validación como control de calidad antes de integrar a producción.

Esto simula, a pequeña escala, el rol que cumple la integración continua (CI) en un pipeline DevOps real: detectar errores automáticamente antes de que lleguen a producción, sin depender de una revisión manual exhaustiva.

---

## 📁 Estructura de carpetas


Lista-de-perros/
├── .github/
│   └── workflows/
│       └── ci.yml
├── index.html
├── index.js
├── style.css
├── .gitignore
└── README.md


---

## 🔧 Cambios simulados en este ciclo de desarrollo

| Rama | Tipo | Descripción |
|---|---|---|
| feature/contador-likes | feature | Agrega un contador visible de likes/dislikes en pantalla. |
| feature/modo-oscuro | feature | Agrega un botón para alternar entre modo claro y modo oscuro. |
| hotfix/fix-imagen-repetida | hotfix | Corrige un bug en el que, si la API entregaba dos veces seguidas la misma imagen, el spinner de carga quedaba visible para siempre (el evento load no se vuelve a disparar si el src no cambia). |

---

## 👥 Autores

- Integrante 1 — Karla Hoch
- Integrante 2 — Sebastian Huaiquimilla

---

## 🤖 Uso de Inteligencia Artificial

> Se utilizó la IA *Claude (Anthropic)* como apoyo en las siguientes tareas:

- Configuración inicial del repositorio: creación de la estructura de ramas (main, develop, feature/*, hotfix/*) y de los cambios de ejemplo tipo feature y hotfix sobre el proyecto base.
- Redacción y estructuración de partes del README.md (convenciones de commits, naming de ramas, criterios de revisión de PR, estructura de carpetas).
- Generación y posterior depuración del workflow de GitHub Actions (.github/workflows/ci.yml) y sus archivos de configuración asociados (.htmlhintrc, .stylelintrc.json).
- Apoyo para resolver errores durante la integración (conflictos de merge y fallos del pipeline de CI).
- Corrección de redacción del párrafo de justificación de la estrategia de ramificación, a partir de las ideas y respuestas entregadas por el equipo.

Todo el contenido generado con apoyo de IA fue revisado y validado por el equipo. Las justificaciones técnicas y las reflexiones individuales de este informe fueron redactadas íntegramente por Karla Hoch y Sebastián Huaiquimilla, sin apoyo de IA.


## 🧠 Reflexiones individuales



- *Karla Hoch:* Me encargué de armar las ramas del repositorio y subirlas a GitHub / trabajar en el HTML y JS del contador de likes y del modo oscuro. Lo que más me costó fue el HTML e index.js, porque no tenía muy fresca esa materia y tuve que rebuscar cómo hacer ciertas cosas. No se me hizo tan complicado y me fui acordando de las cosas mientras las hacia, no tuve muchos errores asi que no tuve que pelear con el codigo.
- *Sebastián Huaiquimilla:* Me encargué de abrir y gestionar los Pull Requests, y trabajar en el hotfix y en revisar style.css. Lo que más me costó fue detectar qué estaba mal en style.css. Con este trabajo aprendí a usar bien el github, a usar los pull request merge y cosas que no sabia usar muy bien, editar los errores en el momento y principalmente a moverme bien en github.

Proyecto original: repaso de conexión a API y manejo de eventos en JavaScript. Adaptado como base para la Evaluación Parcial N°1, DOY0101 — Ingeniería DevOps.