# Estado del Producto Mínimo Viable (PMV) — Aprobado técnicamente

El PMV del proyecto `cr-la-carpio` cuenta con **revisión técnica validada (`2026-11-12`)** tras integrar las contribuciones del equipo interinstitucional de Costa Rica:

- **Geovisor depurado (`/aplicacion/`):** Publica las **7 capas clave solicitadas** sobre la malla de **2,470 hexágonos de 20 m**, acompañadas de las **23 capas abiertas de Copernicus** y del **Tablero Estadístico de Exposición Poblacional** bajo el mapa.
- **Tablas estadísticas auditables (`geovisor/estadisticas/`):** Indicadores principales, distribución en las 5 clases de riesgo, combinaciones excluyentes de amenazas y desglose en los 9 sectores de La Carpio.
- **Atlas Cartográfico Homologado (`/resultados/`):** Portada institucional, introducción del Clúster Copernicus Urbano con enlace al Geovisor, **Parte I** con 4 láminas sobre la malla de 20 m y **Parte II** con 10 láminas satelitales Copernicus (PDF de 27 páginas).
- **Reproducibilidad completa:** Scripts `build_local_multihazard_index.py` y `build_risk_statistics.py`, cuaderno `score_multiamenaza_edificaciones.ipynb` (v1.1) y línea base censal INEC (`docs/censo-uruca-linea-base.md`).
