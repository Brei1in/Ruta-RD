# Ruta-RD

index.html	
Estructura principal y contenedores para el mapa, formulario, resultados y detalles.
app.js	
Lógica central de la aplicación: carga de datos, cálculo de rutas (filtrado por preferencia), manejo de eventos, y gestión de estado (favoritas, idioma, tema).
rutas.json	
Base de datos de rutas disponibles, con origen, destino, tipo de transporte, tiempo y costo. Dato central de la aplicación.
barrios.json
Lista de todos los barrios disponibles como origen o destino.
alerts.json
Lista de alertas actuales mostradas en el panel lateral.
i18n.json	
Diccionario para la traducción de textos a Español (es) e Inglés (en).
service-worker.js / manifest.json
Archivos necesarios para la funcionalidad de PWA (instalación y cacheo offline).
styles.css	
Estilos visuales, incluyendo soporte para el Modo Oscuro.
