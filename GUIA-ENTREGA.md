# Guía para terminar la práctica

## 1. Revisar en local

Extrae el ZIP, abre practica-despliegues en VS Code y ejecuta npm ci y npm start.
Comprueba main, qa-pending y uat-pending con git switch. Cada rama tiene el componente con su mensaje y color.
Ejecuta npm run build si quieres comprobar la compilación local.

## 2. Crear el tablero desde el principio

Consulta TRELLO.md. Crea el tablero, sus seis listas y las nueve tarjetas.
Mueve las tarjetas conforme revises o completes cada trabajo. No simules pruebas que aún no has hecho.
Los pasos del proyecto que ya están preparados también debes revisarlos y entenderlos.

## 3. Subir a GitHub

Crea en GitHub un repositorio vacío llamado practica-entornos, sin README, licencia ni .gitignore iniciales.
Hazlo público para que el profesor pueda consultarlo, o dale acceso si debe ser privado.
Dentro del proyecto ejecuta, sustituyendo TU_USUARIO por tu usuario real:

```bash
git switch main
git remote add origin https://github.com/TU_USUARIO/practica-entornos.git
git push -u origin main
git push -u origin qa-pending
git push -u origin uat-pending
```

GitHub puede pedir autenticación. Comprueba las tres ramas en GitHub y guarda una captura.
Para tus siguientes commits configura tu nombre y correo de Git (usa tu correo privado de GitHub si lo prefieres):

```bash
git config user.name "TU NOMBRE"
git config user.email "TU CORREO"
```

No sustituyas el historial incluido por pruebas inventadas. Consulta el historial real con:

```bash
git log --all --oneline --graph --decorate
```

## 4. Vercel

Importa el repositorio en un proyecto de Vercel. Selecciona Angular y main como rama de producción.
La raíz es la carpeta que contiene package.json, sin subdirectorio si subes este proyecto como raíz.
El archivo vercel.json ya establece npm run build y dist/practica-despliegues/browser.
No actives SSR. Completa el despliegue y abre la URL de producción.

En Deployments localiza o crea los despliegues de qa-pending y uat-pending.
Si no se crean porque las ramas ya existían al importar, utiliza la opción de crear un despliegue para cada rama.
Usa la URL fija de cada rama, que apunta a su último despliegue, para QA y UAT.
No selecciones Promote to Production para esas ramas.

Según el enunciado: Settings > Deployment Protection > desactivar Vercel Authentication y guardar.
Comprueba las tres URL en incógnito y captura cada página con su dirección visible:
main verde, QA naranja y UAT azul. Los nombres de opciones pueden variar en la interfaz.

## 5. Paso .gitignore: después de verificar las tres URL

El profesor pide añadir el componente al .gitignore. El patrón sería:

```gitignore
/src/app/entorno/
```

Pero Git NO deja de controlar archivos que ya están versionados por añadir ese patrón.
Mantén el componente versionado para que Angular pueda compilar al descargar el repositorio.
No ejecutes git rm --cached sobre él: tras confirmar la eliminación, un despliegue limpio no dispondría del componente importado.
Consulta con tu profesor qué solución espera para dejar de detectar cambios locales sin romper los despliegues.
No se ha aplicado skip-worktree ni assume-unchanged: son marcas locales y no resuelven la separación de entornos en el repositorio remoto.

Si el profesor solo pide que aparezca la regla, añádela en las tres ramas DESPUÉS de comprobar las URL:

```bash
git switch main
# Añade la línea indicada en .gitignore desde VS Code.
git add .gitignore
git commit -m "Añadir regla del componente al gitignore"
git push
```

Repite en qa-pending y uat-pending. Documenta que los archivos ya versionados siguen bajo control de Git.
No mezcles las ramas completas entre sí: en esta fase contienen versiones diferentes del indicador.

## 6. Documento final

Completa PLANTILLA-ENTREGA.md en tu editor de documentos y añade las capturas reales.
El enunciado no fija un formato; puedes exportarlo a PDF si tu profesor no indica otro.
Incluye el repositorio, las tres ramas, tres entornos, tres URL, commits, explicación y URL de Trello.
Añade una captura del tablero como evidencia adicional de las listas y tarjetas.
El trabajo NO está terminado hasta que publiques, compruebes los enlaces y completes el documento.
