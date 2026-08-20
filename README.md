# Bali 2026 · app móvil

Itinerario día a día de Bali, Nusa Penida y Gili Trawangan — 5 a 18 de septiembre de 2026, 4 adultos, 13 noches.
PWA instalable, funciona sin conexión. Preparada para GitHub Pages.

## Archivos

| Archivo | Qué es |
| --- | --- |
| `index.html` | La app entera: datos, estilos y lógica en un solo archivo |
| `vendor/leaflet.js` · `vendor/leaflet.css` | Leaflet 1.9.4, servido desde el repo para que el mapa funcione sin CDN |
| `manifest.webmanifest` | Instalación como app |
| `sw.js` | Service worker · caché y modo offline |
| `icon.svg` | Icono |

## Cómo está montada

Todo el itinerario vive en el objeto `APP_DATA` dentro de `index.html`. Los días son arrays
posicionales `[hora, icono, nombre, duración, origen, destino, nota]`, y las coordenadas van
aparte en `APP_DATA.coords`. **Al añadir una parada nueva hay que tocar las dos cosas**, o el
botón de Maps y el pin del mapa se quedan sin sitio al que apuntar.

Los enlaces de navegación abren Google Maps. El mapa interactivo usa Leaflet con teselas de
CARTO sobre datos de OpenStreetMap.

## Al desplegar

Sube todo a la raíz del repositorio y activa GitHub Pages desde `main` / `(root)`.

**Si cambias `index.html`, sube también la versión de `CACHE` en `sw.js`** (`bali-2026-v6` →
`v7`). El service worker cachea de forma agresiva: sin ese cambio, los móviles que ya tengan la
app instalada seguirán viendo la versión antigua indefinidamente.

## Créditos

Fotografías de Wikimedia Commons bajo licencias CC BY, CC BY-SA y CC0; la atribución completa
de cada imagen está dentro de la app, en la pestaña **Viaje**.
Mapas © OpenStreetMap · teselas © CARTO.
