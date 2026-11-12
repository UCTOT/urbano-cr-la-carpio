# Desarrollo técnico reproducible (`cr-la-carpio`)

Espacio versionado con los cuadernos interactivos y scripts en Python (CRTM05 `EPSG:5367` → `EPSG:4326`) que generan las capas publicadas en `geovisor/`, las tablas estadísticas de exposición poblacional y las contribuciones a `atlas/products/`.

## Flujos reproducibles disponibles

### 1. `src/score_multiamenaza_edificaciones.ipynb` (v1.1)
- **Propósito:** Evaluación interactiva de multiamenaza ponderada y exposición de edificaciones (techos) en La Carpio (San José, Costa Rica).
- **Entorno:** Diseñado para ejecutarse directamente en **Google Colab** o Jupyter Notebook local sin dependencia obligatoria de credenciales propietarias.
- **Flujo de trabajo:**
  1. Configuración de entorno geoespacial abierto (`geopandas`, `rasterio`, `rasterstats`, `overturemaps`, `folium`).
  2. Auditoría automática y vinculación directa a las capas homologadas del repositorio GitHub (`perimetro_zona_estudio.geojson`, `CATALOGO_AMENAZAS` y levantamiento de techos).
  3. Proyección métrica en **CRTM05 (`EPSG:5367`)** oficial de Costa Rica con resolución configurable (10 m / 20 m / 30 m).
  4. Contingencia morfológica documentada y descarga abierta de edificaciones de **Overture Maps** o capa local de techos.
  5. Reducción zonal en 5 niveles (*Muy Bajo*, *Bajo*, *Medio*, *Alto*, *Muy Alto*), visualización Folium y exportación `.zip` (GeoTIFF + GeoPackage).

### 2. `scripts/build_local_multihazard_index.py` y `scripts/build_risk_statistics.py`
- **Propósito:** Cálculo determinista del índice local de multiamenaza y restricciones sobre la **malla de 2,470 hexágonos de 20 m** (`malla_hexagonal_20m_poblacion.geojson`), incorporando áreas de protección fluvial como riesgo *Muy alto* (puntaje 100) y deslizamientos `CATEGORIA_` 4–5, más desagregación entera por mayores restos de **30,252 habitantes** en los 9 sectores de La Carpio.
- **Salidas:**
  - `geovisor/capas/indice_multiamenaza_local_20m.geojson` y `geovisor/capas/restricciones_desarrollo_hex_20m.geojson`.
  - Tablas base del tablero estadístico en `geovisor/estadisticas/*.csv`.
