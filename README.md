# Cumple de Coco

Planificador retro adaptable a celulares. La lista se comparte entre quienes abran la página e ingresen la contraseña. Todos pueden editar invitados, marcar quién aporta a Quinta, Comida, Bebida y Alcohol, y agregar, quitar o cambiar cantidades y precios de las compras. Cada persona ve junto a su nombre cuánto debe pagar según las secciones marcadas.

## Acceso compartido y Supabase

El proyecto ya está conectado a Supabase. `config.js` contiene la URL del proyecto y su clave pública `anon` (es normal que esta clave esté en una página web). La tabla `public.coco_party_state` conserva el estado común.

La contraseña compartida es **cococumple**. Supabase valida la contraseña en funciones RPC y guarda solo su hash; la contraseña no está escrita en el HTML ni se guarda en el navegador. La tabla no permite acceso directo anónimo. No uses esta lista para información privada: quienes tengan la contraseña pueden cambiar o borrar el contenido compartido.

Para cambiar la contraseña, modifica el hash en `private.coco_party_access` desde Supabase SQL Editor. No reemplaces las funciones RPC ni abras permisos directos a la tabla.

## Publicar o actualizar en GitHub Pages

1. En GitHub, crea un repositorio público, por ejemplo `cumple-coco`.
2. En el repositorio, pulsa **Add file → Upload files** y sube `index.html`, `config.js` y `README.md`.
3. Pulsa **Commit changes** para guardar los archivos.
4. Abre **Settings → Pages**. En **Build and deployment**, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y pulsa **Save**.
5. Comparte la URL que aparece en esa pantalla y la contraseña **cococumple** con los invitados.

Si ya publicaste el sitio, vuelve a subir esos tres archivos con **Add file → Upload files** y confirma el commit. GitHub Pages actualizará el sitio automáticamente. El estado de Supabase permanece guardado aunque publiques una versión nueva.

La página actualiza la lista compartida cada cinco segundos y guarda los cambios automáticamente. El estimado de comida propone cantidades fijas para mediodía y noche (dos hamburguesas por persona); al sumar participantes, la página avisa si las compras cargadas no alcanzan.