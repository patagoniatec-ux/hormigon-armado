# Hormigón Armado · CET Nº 33

Primera arquitectura de un aula digital para Maestro Mayor de Obras. Diseño fiel a la propuesta aprobada: blanco, gris, petróleo, cabecera institucional, imagen estructural y tarjetas de tres columnas. No necesita instalación de paquetes ni compilación.

## Páginas

Inicio, unidades, material de consulta, trabajos prácticos, proyecto integrador, INET, Hormigón en movimiento, calendario, libro de temas, galería, red de colaboradores y contacto. El inicio toma el último tema por fecha y las próximas fechas del contenido. La galería tiene filtros por Planos y CAD, Maquetas y Expo, con apertura ampliada. Las fichas de colaboradores permiten portada, logo, descripción y contactos.

## Abrir localmente

Desde la raíz del proyecto:

```sh
python3 -m http.server 8000 --directory dist
```

Abrir `http://localhost:8000`. Usar un servidor: abrir los HTML con file:// no permite cargar el JSON de manera fiable.

## Administración en esta primera versión

`dist/admin.html` es un **editor de borradores locales**, no un CMS conectado ni un área autenticada. Permite editar el inicio, títulos, fechas, unidades, materiales, colaboradores e imágenes; crear, eliminar y ordenar registros; cargar varias imágenes juntas; guardar en IndexedDB; importar y exportar contenido.

1. Editar y pulsar **Aplicar al borrador** en cada formulario.
2. Pulsar **Guardar borrador**. Esto guarda solo en ese navegador y dispositivo.
3. **Vista previa** muestra el borrador mediante `?preview=1`.
4. **Exportar contenido** descarga `content.json`.
5. Para publicar los cambios, reemplazar `dist/data/content.json` en GitHub y volver a desplegar.

Las imágenes se convierten en WebP hasta 1800 px y se incluyen en el JSON como datos. Es una solución inicial portable; para una galería grande se debe conectar almacenamiento de imágenes separado. No cargar datos privados: todo archivo incorporado al repositorio público será público.

## Contenido

`dist/data/content.json` es la única fuente publicada de contenido. Flexión en vigas y las tres unidades son ejemplos claramente marcados; no se inventaron fechas, empresas, alumnos, fotos de trabajos ni documentos. Los recursos, eventos y galería quedan listos para recibir material real. Los enlaces a Instagram, al portal y el correo se configuran desde el editor; inicialmente están vacíos. Las imágenes de portada proceden de las propuestas visuales aprobadas y son ilustrativas.

## Estructura

- `dist/*.html`: páginas y editor.
- `dist/styles.css`: diseño responsive.
- `dist/app.js`: lectura y presentación del sitio.
- `dist/admin.js`: formularios, carga de imágenes y manejo de borradores.
- `dist/data-store.js`: validación y persistencia local.
- `dist/data/content.json`: contenido publicado.
- `dist/assets/`: referencias visuales usadas en portada y tarjetas.
- `netlify.toml`: publicación de `dist` sin build.
- `.openai/hosting.json`: configuración de la primera vista alojada.

## GitHub y hosting

Repositorio: [patagoniatec-ux/hormigon-armado](https://github.com/patagoniatec-ux/hormigon-armado). El código de esta primera versión está organizado para continuar el desarrollo sin modificar otros proyectos. Puede publicarse en Netlify con directorio `dist` y sin comando de compilación. Para GitHub Pages, publicar el contenido de `dist`, no la raíz del proyecto.

## Próxima etapa

Conectar un CMS con autenticación docente, persistencia compartida y almacenamiento de imágenes. La interfaz de edición ya está preparada, pero guardar no publica hasta implementar esa conexión. La propuesta de tutor permanece pendiente de definir; esta versión no simula un servicio de IA.

## Noticias y actualidad

noticias.html y el inicio presentan la colección news por fecha descendente. Incluye buscador y filtros por Hormigón y materiales, Estructuras y obras, Normativa, Innovación y Aula y visitas. Las fichas admiten título, descripción, fecha, categoría, fuente, enlace original, texto completo e imagen opcional. Se cargan desde Noticias y actualidad en el editor. Guardar conserva el borrador local; para publicar, exportar y reemplazar dist/data/content.json en GitHub. Los borradores antiguos se migran sin perder sus contenidos. La colección comienza vacía, lista para notas reales.
