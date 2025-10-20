1. CSS (estilos) 
Este archivo define los estilos visuales de la aplicación, incluyendo temas claro/oscuro, responsividad y accesibilidad.

Variables CSS (:root): Define colores base como (fondo), (texto), (azul acento), etc. Estas variables cambian automáticamente para modo oscuro usando .--bg--fg--accent@media (prefers-color-scheme: dark)
Modo Oscuro Manual: Con la clase en , se aplican colores oscuros manualmente..dark:root
Animaciones Reducidas: Para usuarios con , se desactiva la transición.prefers-reduced-motion
Reset y Base: Estilos básicos para , , incluyendo fuente (Inter), layout flex y suavizado de fuentes.htmlbody
Transiciones: Aplica transiciones suaves a botones, tarjetas, etc., para mejor UX.
Header: Estilos para el encabezado, logo (con gradiente), y controles (botones de idioma, tema, ahorro).
Botones e Inputs: Estilos para botones, inputs, selects, con foco accesible (outline azul).
Diseño: Grid responsivo (1 columna en móviles <900px), tarjetas con sombras.
Resultados y Rutas: Estilos para listas de rutas, badges, botones de favoritos.
Alertas: Estilos adaptables con y , que cambian por tema. Variaciones para success, warning, error, info.--alert-bg--alert-border
Minimapa: Contenedor para SVG.
Modo Ahorro: Oculta imágenes y desactiva transiciones cuando se activa.
Pie de página: Estilos simples.
El CSS usa para mezclar colores dinámicamente, asegurando contraste y adaptación a temas.color-mix()

2. HTML (index.html)
Estructura la página web.

Head: Meta tags para viewport, título, descripción, manifest para PWA, iconos, y enlace al CSS.
Body: Contenedor principal con header, main y footer.
Header: Logo, título, y controles (botones para idioma, tema, ahorro).
Main: Sección de búsqueda (formulario con origen, destino, preferencia) y panel derecho (minimap, alertas, favoritos).
Pie de página: Créditos.
Script: Carga como módulo.app.js
Incluye atributos ARIA para accesibilidad (ej. , ).role="banner"aria-label

3. JavaScript (app.js)
Lógica principal de la aplicación.

Estado Global (state): Objeto con barrios, rutas, alertas, diccionario de idiomas, idioma actual, favoritos y modo ahorro.
Inicialización: Al cargar DOM, carga datos JSON, renderiza elementos, registra Service Worker, aplica idioma/tema.
Eventos: Maneja submit de formulario, swap de inputs, toggle de idioma/tema/ahorro.
Carga de Datos: Fetch a archivos JSON locales (barrios, rutas, alertas, i18n).
Renderizado:
renderBarrios(): Llena datalist con opciones de barrios.
renderAlerts(): Muestra alertas en el panel.
renderFavs(): Lista favoritos guardados.
renderMinimap(): Dibuja SVG simple con puntos y línea.
renderRutas(): Muestra rutas filtradas y ordenadas.
Búsqueda: valida inputs, calcula rutas, renderiza resultados.handleSearch()
Favoritos: y gestionan localStorage.saveFav()removeFav()
Idioma: cambia idioma, actualiza textos con .toggleLang()applyLang()data-i18n
Tema: alterna clase , guarda en localStorage.toggleTheme().dark
Modo Ahorro: añade clase al body.toggleLowData()low-data
Service Worker: Registra SW para offline.
Funciones globales expuestas para eventos inline en HTML.

4. Datos JSON
Archivos de datos estáticos.

barrios.json: Array de strings con nombres de barrios (ej. "Gazcue").
rutas.json: Array de objetos con id, origen, destino, tipo (carro público, etc.), tiempo (min), costo (RD$).
alerts.json: Array de objetos con tipo y mensaje (ej. lluvia, tráfico).
i18n.json: Objeto con traducciones para "es" y "en" (títulos, botones, etc.).
5. Trabajador de servicios (service-worker.js)
Maneja caching para PWA.

Instalación: Cachea archivos esenciales (HTML, CSS, JS, datos, manifest).
Activación: Elimina caches viejos.
Fetch: Primero intenta red, luego cache; guarda respuestas en cache.
6. Manifiesto (manifest.json)
Configura la PWA.
Nombre, íconos, colores, URL de inicio, modo display (standalone).

Funcionalidad General
Búsqueda: Usuario selecciona origen/destino, app filtra rutas de JSON, muestra ordenadas por tiempo.
Interactividad: Swap inputs, guardar favoritos, ver alertas.
Personalización: Tema, idioma, ahorro.
Offline: SW permite uso sin internet.
Instalación: Como app nativa.
