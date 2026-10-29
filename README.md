# Práctica 2: Simulación Release Manager

Proyecto Angular sencillo, sin SSR ni rutas. El componente EntornoComponent está anidado en App.

## Empezar

Necesitas Node.js 22.12 o superior compatible con Angular 20 y Git.
Abre una terminal dentro de esta carpeta:

```bash
npm ci
npm start
```

Abre http://localhost:4200. Para detener el servidor: Ctrl+C.

## Ramas incluidas

El ZIP incluye el repositorio local .git con commits de preparación y estas ramas:

| Rama | Mensaje | Color |
| --- | --- | --- |
| main | Entorno de producción | Verde |
| qa-pending | Entorno de pruebas QA | Naranja |
| uat-pending | Entorno de aceptación UAT | Azul |

```bash
git branch
git switch qa-pending
npm start
```

Detén el servidor antes de cambiar de rama. Vuelve a ejecutar npm start para ver cada versión.
La carpeta .git puede estar oculta: conserva esa carpeta al extraer el ZIP.
No ejecutes git init de nuevo ni borres .git. Si desaparece, faltarán las ramas y el historial.
Los commits incluidos son preparación generada del proyecto; revisa el código y añade tus propios cambios.

## Archivos que debes entender

- src/app/app.ts: importa el componente hijo.
- src/app/app.html: muestra título, bienvenida y la etiqueta app-entorno.
- src/app/entorno/: muestra el mensaje, rama y color de cada entorno.
- vercel.json: indica el comando de compilación y la carpeta estática resultante.
- GUIA-ENTREGA.md: publicación, capturas y lista de comprobación.
- TRELLO.md: listas y nueve tarjetas con sus descripciones.
- PLANTILLA-ENTREGA.md: estructura para redactar tu documento con evidencias reales.

El nombre local del proyecto es practica-despliegues y el repositorio de GitHub debe llamarse practica-entornos.
No hay URLs publicadas, capturas de Vercel ni un tablero Trello creado todavía.

## Sobre .gitignore

El enunciado solicita añadir el componente al .gitignore después de comprobar los despliegues.
Todavía no se ha realizado ese paso porque depende de tus comprobaciones reales.
La guía incluye el patrón y explica la limitación de Git: un archivo ya versionado sigue controlado aunque aparezca en .gitignore.
