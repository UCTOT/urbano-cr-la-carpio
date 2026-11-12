# Metodología integrada: Malla hexagonal de 20 m, índice multiamenaza, línea base INEC y cuaderno reproducible

El flujo metodológico aprobado por el equipo interinstitucional de Costa Rica (**MSJ · MIVAH · INVU**) combina cálculos métricos exactos en **CRTM05 (`EPSG:5367`)**, calibración demográfica satelital-local, contexto censal oficial del **INEC** y herramientas abiertas en Python / Google Colab.

## 1. Calibración habitacional y línea base censal INEC (Uruca `10107`)

- **Contraste satelital-local:** Se calibraron las huellas de **Google Open Buildings v3** frente al levantamiento local de techos (concordancia `ratio = 0.988`) mediante un modelo *piecewise* con factor base de **4.5 personas/vivienda** sobre **2,470 hexágonos de 20 m** (`malla_hexagonal_20m_poblacion.geojson`, suma de `5,459.9` viviendas estimadas).
- **Distribución demográfica sectorial (`30,252` habitantes):** La población del escenario sectorial (`pob_alta_5_4_hab`) se reparte entre los hexágonos de cada uno de los **9 sectores** proporcionalmente a las viviendas estimadas y al área de intersección, aplicando redondeo por **mayores restos** para preservar exactamente la suma entera de cada sector (`pob_esc_5_4_hab`).
- **Contexto intercensal INEC (2011–2022):** Se integra la serie oficial del distrito Uruca (`10107`): crecimiento de **31,728 hab (2011)** a **43,484 hab (2022, +37.1%)** y diferencial positivo de ocupación por vivienda (**3.8** en 2011 y **~3.3–3.5** en 2022 frente a **3.1** nacional), documentado en `docs/censo-uruca-linea-base.md`.

## 2. Índice local de multiamenaza y restricciones en hexágonos de 20 m

Ejecutado mediante `scripts/build_local_multihazard_index.py` y resumido estadísticamente con `scripts/build_risk_statistics.py`:

- **Susceptibilidad a deslizamientos (`CATEGORIA_` 4 y 5):** Ingresan al puntaje las categorías **ALTA (4, peso 0.75)** y **MUY ALTA (5, peso 1.0)** ponderadas por fracción de área del hexágono de 20 m (`desliz_score_0_1`). Las categorías 1–3 aportan cero al índice pero se registran en cobertura descriptiva.
- **Inundación potencial (`inundacion_potencial_pct`):** Fracción porcentual del hexágono que intersecta la huella cartográfica de inundación potencial.
- **Protección fluvial (Ley Forestal 7575):** Las celdas que intersectan `proteccion_rios.geojson` reciben directamente condición **Muy alto (índice = 100)** por presencia de población asentada en retiros fluviales (**588 hexágonos · 4,687 habitantes · 15.49%**).
- **Capa de restricciones (`restricciones_desarrollo_hex_20m.geojson`):** Destaca las **1,523 celdas** que intersectan protección fluvial (verde: 21 hex), amenaza por deslizamiento 4–5 (rojo: 935 hex) o el solape de ambas condiciones (morado: 567 hex).

## 3. Cuaderno interactivo de edificaciones (`src/score_multiamenaza_edificaciones.ipynb` v1.1)

Permite auditar en tiempo real las capas del repositorio GitHub desde **Google Colab** o Jupyter local, cruzar amenazas vectoriales/ráster con edificaciones de techos locales u **Overture Maps** y exportar resultados en GeoTIFF y GeoPackage.
