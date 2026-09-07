# Almacén Central · Panel de Inventario

Dashboard estático (sin JavaScript) hecho con **HTML + CSS puro**, que muestra
KPIs de inventario, un gráfico de barras, un donut de distribución, alertas de
stock bajo y una tabla de movimientos recientes. Todos los datos están
escritos a mano en el HTML (no hay lógica dinámica ni conexión a una base de
datos).

## 📁 Archivos del proyecto

```
├── index.html    → Estructura y contenido del dashboard
├── styles.css    → Todos los estilos (colores, layout, responsive)
└── README.md     → Este archivo
```

**Los dos archivos (`index.html` y `styles.css`) deben estar SIEMPRE juntos,
en la misma carpeta.** El HTML enlaza el CSS con una ruta relativa:

```html
<link rel="stylesheet" href="styles.css">
```

Si el archivo `styles.css` no está en la misma carpeta que `index.html`
(por ejemplo, si solo copiaste o enviaste el HTML por separado), el
navegador no encontrará los estilos y verás la página sin ningún diseño,
aunque el HTML funcione bien.

## ▶️ Cómo abrirlo

No necesita servidor ni instalación: basta con hacer doble clic en
`index.html`, o abrirlo desde el navegador (`Archivo > Abrir`). También
funciona subiendo ambos archivos a cualquier hosting estático (GitHub Pages,
Netlify, un servidor propio, etc.).

## 🖥️ Diseño responsive

El layout se adapta en 3 puntos de quiebre (breakpoints), definidos al final
de `styles.css`:

| Breakpoint | Dispositivo típico | Qué cambia |
|---|---|---|
| `≤ 1080px` | Tablet horizontal / laptop chico | Los paneles de 2 columnas pasan a 1; los 4 KPIs se acomodan en 2×2; el sidebar se angosta. |
| `≤ 780px` | Tablet vertical / móvil grande | El sidebar pasa de columna vertical a barra horizontal desplazable; se ocultan etiquetas de grupo y el estado de sincronización; el buscador baja al final de la topbar. |
| `≤ 480px` | Celular | Los KPIs se apilan en 1 columna; se ocultan nombre y rol del usuario (queda solo el avatar); se reducen fuentes, iconos y espaciados. |

La tabla de "Movimientos recientes" está envuelta en un contenedor
(`.table-wrap`) con scroll horizontal, para que sus columnas nunca se
aplasten en pantallas angostas.

## 🛠️ Troubleshooting

**"En el computador se ve bien, pero en la tablet/celular aparece sin
estilos"** — casi siempre es uno de estos motivos:

1. **Falta el `styles.css` en la carpeta.** Si compartiste el HTML por
   WhatsApp, correo o Drive sin la carpeta completa, el CSS no viaja con él.
   Copia o comparte ambos archivos juntos.
2. **Mayúsculas/minúsculas distintas.** Windows/Mac suelen ignorar
   mayúsculas en nombres de archivo, pero Android/iOS no. Verifica que el
   archivo se llame exactamente `styles.css` (todo en minúsculas).
3. **Caché del navegador.** Si antes hubo un error de carga, el navegador
   puede haberlo guardado en caché. Prueba recargar forzado o abrir en una
   pestaña de incógnito.
4. **Servidor local con rutas distintas.** Si usas algo como Live Server y
   accedes desde la tablet por otra IP/puerto, confirma que esa misma ruta
   sirva también el `styles.css`.

## 🎨 Personalización rápida

Todos los colores, radios de borde y sombras están centralizados como
variables CSS en `:root` (arriba de `styles.css`). Cambiar un valor ahí
actualiza automáticamente todo el dashboard, por ejemplo:

```css
--primary:#5B5FEF;   /* color de marca / acentos */
--amber:#F2A93C;      /* alertas de stock bajo */
--red:#EF5B5B;        /* alertas críticas */
--teal:#17C3A2;       /* estados positivos */
```

Si cambias los porcentajes de la distribución por categoría en el HTML
(`.donut-legend`), recuerda actualizar también los mismos rangos en el
`conic-gradient` de `.donut` en `styles.css` — ese gráfico no se genera
automáticamente a partir del HTML.
