# Geocodificador Territorial de Santiago

Herramienta complementaria de GIS STGO.

## Uso
Importar un CSV o XLSX con `DIRECCION` o `CALLE` y `NUMERO`. Solo si la búsqueda automática no localiza la dirección podrá emplearse `COORD_GOOGLE` (latitud, longitud), siempre que exista límite comunal validado.

## Bases
- **Callejero con numeración:** Azimut / Maestro de Calles IDE Chile 2022, a través de `callejero-segments-index.json`. Se usa exclusivamente la clave de comuna `santiago`, con registros `c, v, n, g`. Requiere conectividad y acceso CORS a la fuente. No es todavía una copia alojada en HERRAMIENTAS.
- **Límite comunal:** `datos/limite_comunal.geojson` (1 polígono), copia de `PHDGEOGRAFO/VISOR-REPOSITORIO-DIGITAL/public/data/comuna.geojson`.
- **Barrios municipales:** `datos/barrios.geojson` (27 polígonos), copia de `PHDGEOGRAFO/VISOR-REPOSITORIO-DIGITAL/public/data/barrios.geojson`.
- **Territorios municipales:** `datos/territorios.geojson` (6 polígonos), reutilizados de la versión municipal del visor turístico Santiago de octubre de 2026. Revisar contra base territorial maestra ante posteriores modificaciones.

El navegador carga automáticamente estas tres capas sin intervención del usuario, identifica barrio y territorio mediante intersección y valida los puntos dentro del límite comunal. Los límites deben revisarse frente a su fuente maestra en cada actualización territorial.

## Calidad
Los resultados son **INTERPOLADA** (nunca exactos por el solo hecho de estar dentro del rango), **MANUAL GOOGLE** o **NO LOCALIZADA**. Dos o más tramos compatibles generan revisión en vez de elegir un punto arbitrario.

## Exportaciones
CSV de auditoría y GeoJSON. El GeoPackage directo todavía necesita motor de exportación específico.

## Fuentes y licencias
Azimut de Jorge Ulloa Roa, repositorio: https://github.com/geoidegeoidal/azimut (licencia MIT). Maestro de Calles IDE Chile 2022. Para datos basados en OpenStreetMap, respetar atribución y ODbL.
