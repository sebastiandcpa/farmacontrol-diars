# FarmaControl

Demostración académica del sistema de gestión de ventas, compras e inventario de farmacia, basada en el PDF y los archivos del proyecto DIARS.

**Abrir la aplicación:** https://sebastiandcpa.github.io/farmacontrol-diars/

Esta versión está pensada para abrir un enlace y explicar el proyecto durante una exposición. El aspecto visual sigue la referencia verde y blanca del informe. Funciona como aplicación estática con datos ficticios y persistencia en el navegador; **no se conecta a SQL Server ni tiene un backend de autenticación**.

## Funciones disponibles

- Ingreso por cuatro perfiles de demostración y navegación según sus tareas.
- Resumen de ventas, existencias y alertas.
- Registro y edición de clientes, con validación de documentos duplicados.
- Registro y edición de medicamentos; creación de lotes.
- Compras con varios lotes e incremento de existencias.
- Ventas por lote, descuento de stock y comprobante simulado imprimible.
- Validación de cantidades, vencimiento y referencia de receta vigente del cliente.
- Anulación de ventas con reversión de existencias una sola vez.
- Registro de referencias de recetas por el perfil farmacéutico.
- Alertas de existencias agotadas, stock bajo y vencimientos en 30 días.
- Reportes con periodo de consulta, indicadores calculados y exportación CSV.
- Perfiles de muestra que pueden activarse o desactivarse.
- Documentación técnica y guion de exposición en los archivos del repositorio.
- Datos iniciales disponibles al abrir el sitio en un navegador sin registros previos.

Los datos quedan en `localStorage`: recargar conserva las operaciones. Cada navegador mantiene su propia demostración. La selección de perfil simula responsabilidades de interfaz y **no es una barrera de seguridad**.

## Tecnologías de esta versión

| Capa | Tecnología | Uso |
| --- | --- | --- |
| Estructura | HTML5 | Pantallas, formularios y tablas |
| Presentación | CSS3 | Diseño adaptable inspirado en el informe |
| Interacción | JavaScript con módulos ES | Navegación y reglas del negocio |
| Persistencia de la demo | localStorage | Datos guardados en el navegador |
| Pruebas de reglas | Node.js y node:test | Compras, ventas y validaciones |
| Publicación | GitHub Pages | Sitio estático sin compilación |
| Diseño de base de datos | SQL Server 2019 o posterior | Script fuente independiente incluido |

No utiliza React, Angular, Next.js ni un servidor de base de datos durante la navegación. Node.js es únicamente una herramienta opcional para servir la demo localmente y ejecutar las pruebas.

## Ejecutar localmente

Con Node.js 20 o posterior, desde esta carpeta:

```sh
node server.mjs
```

Abrir `http://localhost:4173`. No se necesita instalar dependencias. Los módulos JavaScript deben servirse mediante HTTP; no abrir `index.html` con doble clic.

## Ejecutar pruebas

```sh
node --test tests/domain.test.mjs
```

Las pruebas verifican las reglas de la demo JavaScript. No prueban la ejecución del script T-SQL ni sustituyen pruebas de una aplicación conectada a SQL Server.

## Publicación

### GitHub Pages

En Settings → Pages seleccionar Deploy from a branch, rama `main`, carpeta `/ (root)`. La aplicación usa rutas con `#` y archivos relativos para funcionar bajo el nombre del repositorio. `.nojekyll` permite publicar los archivos directamente.

### Vercel

Importar este repositorio, seleccionar el preset **Other**, sin comando de compilación ni instalación y con directorio de salida `.`. El archivo `vercel.json` contiene la configuración del sitio estático. No son necesarias variables de entorno para esta demo. Publicar en Vercel no agrega una conexión a SQL Server.

## Base de datos del proyecto

`database/FarmaControl_SQLServer.sql` conserva el script original del ZIP proporcionado por el equipo. Incluye 13 tablas, los tipos de detalle, índices, tres procedimientos de registro/anulación y tres vistas de consulta. Ejecutar en SQL Server Management Studio sobre una instalación de pruebas nueva siguiendo los comentarios del archivo.

Los diagramas originales se encuentran en `docs/`. Para una aplicación conectada, el siguiente desarrollo debe incorporar API, autenticación, autorización en servidor y conexión segura a SQL Server; el navegador no debe acceder directamente a la base de datos.

## Organización

```text
index.html                    Entrada de la aplicación
styles.css                    Diseño y adaptación a celulares
app.js                        Pantallas, formularios e interacción
domain.js                     Datos de muestra y reglas del negocio
database/                     Script original de SQL Server
docs/                         Diagramas originales
tests/                        Pruebas automatizadas de reglas
GUIA_EXPOSICION.md             Guion sugerido para el video
server.mjs                    Servidor local opcional
vercel.json                   Configuración de alojamiento estático
```

## Alcance académico

Los nombres, documentos y operaciones de la aplicación son ficticios. Los comprobantes no son válidos ante SUNAT. No se procesan pagos ni se hace evaluación clínica de recetas. El avance funcional de una aplicación conectada a la base de datos debe verificarse por separado con los criterios del docente; esta demo no acredita por sí misma dicho avance.
