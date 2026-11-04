# Geocodificador Territorial de Santiago

Herramienta complementaria de GIS STGO.

## Uso
Importar un CSV o XLSX con `DIRECCION` o `CALLE` y `NUMERO`. Solo si la búsqueda automática no localiza la dirección podrá emplearse `COORD_GOOGLE` (latitud, longitud), siempre que exista límite comunal validado.

## Bases
- **Callejero con numeración:** Azimut / Maestro de Calles IDE Chile 2022, a través de `callejero-segments-index.json`. Se usa exclusivamente la clave de comuna `santiago`, con registros `c, v, n, g`. Requiere conectividad y acceso CORS a la fuente. No es todavía una copia alojada en HERRAMIENTAS.
- **Límite oficial:** ubicación prevista `datos/limite_comunal.geojson`. Aún no publicado.
- **Barrios oficiales:** ubicación prevista `datos/barrios.geojson`. Aún no publicado.
- **Territorios oficiales:** ubicación prevista `datos/territorios.geojson`. Aún no publicado.

El navegador carga automáticamente cualquier GeoJSON publicado en estas rutas. Sin límite comunal oficial, las coordenadas interpoladas están respaldadas por la comuna que declara la base IDE, pero **no** tienen validación de intersección espacial; en ese caso `COORD_GOOGLE` no se acepta. Sin barrios o territorios oficiales, sus respectivos atributos se dejan vacíos.

## Calidad
Los resultados son **INTERPOLADA** (nunca exactos por el solo hecho de estar dentro del rango), **MANUAL GOOGLE** o **NO LOCALIZADA**. Dos o más tramos compatibles generan revisión en vez de elegir un punto arbitrario.

## Exportaciones
CSV de auditoría y GeoJSON. El GeoPackage directo todavía necesita motor de exportación específico.

## Fuentes y licencias
Azimut de Jorge Ulloa Roa, repositorio: https://github.com/geoidegeoidal/azimut (licencia MIT). Maestro de Calles IDE Chile 2022. Para datos basados en OpenStreetMap, respetar atribución y ODbL.
