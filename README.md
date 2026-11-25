# Taipéi planner

Planificador de rutas por Taipéi para el 25 de noviembre y del 9 al 11 de diciembre de 2026. Es una web estática: un solo `index.html` con dos hojas de estilo, sin dependencias ni paso de build.

## Qué hace

- Mapa esquemático de Taipéi (ríos y líneas de MRT dibujados en SVG) con la ruta de cada día, paradas numeradas y etiquetas que se colocan solas para no solaparse.
- Lista de paradas por día: arrastrar para reordenar o mover a otro día, subir/bajar, quitar, cambiar la duración y la hora de salida.
- Añadir sitios desde un catálogo o marcándolos en el mapa.
- Recalcula horas de llegada, vuelta a casa, minutos de trayecto y kilómetros; avisa del atardecer y de sitios cerrados a esa hora.
- Deshacer, copiar el plan como texto y volver al plan inicial. Los cambios se guardan en `localStorage`.

## Archivos

| Archivo | Qué es |
| --- | --- |
| `index.html` | La página: marcado, estilos de la página y toda la lógica en JavaScript |
| `tokens.css` | Tokens de diseño (colores, tipografía, espaciado) del tema «Neón claro» (colores vivos sobre base clara) |
| `base.css` | Reglas base de Hallmark (foco, overflow, movimiento reducido) |

## Ejecutar en local

Ábrelo con cualquier servidor estático, por ejemplo:

```bash
python3 -m http.server 8000
# o
npx serve .
```

y visita `http://localhost:8000`. Abrir `index.html` directamente también funciona en la mayoría de navegadores.

## Publicar en GitHub Pages

1. Crea un repositorio y sube estos archivos a la raíz de la rama `main`.
2. En el repositorio: Settings → Pages → Source: "Deploy from a branch", rama `main`, carpeta `/ (root)`.
3. La web queda en `https://<usuario>.github.io/<repositorio>/`.

## Notas

- Los tiempos de trayecto son estimaciones por distancia en línea recta (×1,3): a pie por debajo de unos 900 m, y si no, MRT o taxi con 8 minutos de espera incluidos.
- El mapa es un esquema aproximado, no un mapa a escala de calle.
- Tipografías: Bricolage Grotesque (títulos y cifras) y Albert Sans (texto), desde Google Fonts.
- Para cambiar el plan inicial o el catálogo de sitios, edita `PLACES` e `initial()` en el `<script>` de `index.html`. Si cambias el plan inicial, sube también la constante `KEY` para que el navegador no cargue la versión guardada antigua.
- Diseño hecho con la skill [Hallmark](https://github.com/nutlope/hallmark).
