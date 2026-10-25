# BAÚL — Biblioteca de conocimiento personal

Sitio web estático en español, sin frameworks, servidores ni claves API. Curado a partir de las lecturas y recursos que organizamos para ocho áreas de estudio: filosofía, economía, política, inversiones, relaciones, startups de software, software/datos/IA y finanzas cuantitativas.

## Qué incluye

- **179 entradas** distribuidas en **8 áreas** (175 recursos únicos; algunas lecturas figuran en más de un área).
- Dos niveles de biblioteca por área: **lectura básica** (P1 + P2) y **luego de la base** (P3).
- Tres prioridades: **P1 Esencial**, **P2 Importante**, **P3 Profundización**.
- Rutas de inicio con una selección de libros por área.
- Búsqueda global, filtros por prioridad, tipo y estado, y ordenación.
- Estado de cada recurso: pendiente, en curso, terminado.
- Guardados personales, notas por recurso y posibilidad de añadir recursos propios.
- Exportación e importación JSON del progreso, notas y recursos propios.
- Tema claro/oscuro, diseño móvil y soporte offline tras primera visita (PWA cuando se accede vía HTTPS o localhost).

## Uso local

Abrir `index.html` en el navegador. Si querés probar la app como PWA (incluido funcionamiento offline), ejecutá un servidor local desde esta carpeta:

```bash
python3 -m http.server 8000
```

Entrá en `http://localhost:8000/`.

## Publicar gratis: GitHub Pages

1. Creá un repositorio **público** en GitHub, por ejemplo `baul-conocimiento`.
2. Subí **el contenido de esta carpeta** a la raíz del repositorio: `index.html`, `styles.css`, `app.js`, `data.js`, `sw.js`, `icon.svg` y `manifest.webmanifest`. También podés subir este README.
3. En GitHub: **Settings → Pages → Build and deployment → Deploy from a branch**.
4. Elegí **main** y la carpeta **/(root)**; guardá.
5. Cuando GitHub termine la publicación, la URL será de este estilo: `https://TU-USUARIO.github.io/baul-conocimiento/`.

GitHub Pages es gratuito para repositorios públicos con GitHub Free. La dirección exacta se muestra en Settings → Pages.

## Alternativas gratuitas

- **Cloudflare Pages:** creá un proyecto de Pages y utilizá Direct Upload con estos archivos, o conectá el repositorio Git. Servir archivos estáticos no necesita Functions.
- **Netlify Free:** desplegá la carpeta directamente mediante drag & drop o conectá el repositorio. El plan gratuito tiene límites de créditos y uso.

## Editar el catálogo

Todas las áreas y recursos están en `data.js` bajo `window.KNOWLEDGE_VAULT`. Cada recurso incluye:

```js
{
  "id": "identificador-estable",
  "area": "software",
  "priority": 1,
  "title": "Nombre del recurso",
  "author": "Autor o fuente",
  "why": "Qué aporta a la ruta",
  "kind": "Libro",
  "url": "https://...", // opcional; sin URL se ofrece una búsqueda de libros
  "difficulty": "Intermedio"
}
```

Usá **IDs estables**. El avance y las notas se vinculan al `id`; si cambiás ese campo, la app no asociará el progreso anterior. Si el mismo libro aparece en distintas áreas con el mismo `id`, comparte estado y notas. Podés agregar recursos desde la propia interfaz, sin editar código, pero esos recursos se almacenan localmente.

Si publicás una versión nueva y no ves los cambios inmediatamente, recargá la página (el service worker usa una caché local). Para cambios importantes, cambiá la constante `CACHE` en `sw.js`.

## Datos y privacidad

**No hay backend, cuentas ni sincronización entre dispositivos.** El estado, los favoritos, las notas y los recursos añadidos se guardan con `localStorage` en el navegador y origen web donde abrís el sitio. Si cambiás de dispositivo o dominio, **exportá un JSON** desde el dispositivo de origen e importalo desde el destino. Un borrado de datos del navegador puede eliminar el progreso no respaldado.

El catálogo y el código estarán visibles si usás GitHub Pages con repositorio público. No guardes notas privadas dentro de `data.js` o del repositorio. Las notas que agregás en la interfaz quedan únicamente en el almacenamiento local.

## Mantenimiento y fuentes

La clasificación de prioridades es una **curaduría pedagógica**, no un ranking objetivo de corrientes o autores. Las recomendaciones se nutren de nuestra conversación y pueden contener ediciones bibliográficas o enlaces que cambien con el tiempo. Los libros sin enlace propio ofrecen una búsqueda bibliográfica en Google, no una copia del contenido ni una promesa de disponibilidad gratuita.

Los recursos de investigación o documentación cambiante deben consultarse en su sitio oficial antes de implementar un proyecto, especialmente en IA, legislación, finanzas, APIs y herramientas cloud.
