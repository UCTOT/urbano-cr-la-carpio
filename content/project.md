# La Carpio: evaluación microterritorial en malla de 20 m para el Plan Maestro de Intervención Urbanística Integral

**Equipo técnico interinstitucional colaborador (Costa Rica — MSJ · MIVAH · INVU):** Rodolfo Bolaños Bermúdez, Emiler Segura López, Victoria Delgado Fernández, Jaqueline Vargas Bogantes y Jonnathan Obando Artiaga.

La iniciativa articula información geoespacial de micro-escala, observación satelital Copernicus y registros municipales de emergencia en **La Carpio (distrito Uruca, San José)** para respaldar la formulación e implementación de su **Plan Maestro de Intervención Urbanística Integral** entre la **Municipalidad de San José (MSJ)**, el **Ministerio de Vivienda y Asentamientos Humanos (MIVAH)** y el **Instituto Nacional de Vivienda y Urbanismo (INVU)**.

## Ámbito territorial y unidad de análisis aprobada

- **Ubicación:** Asentamiento La Carpio, distrito Uruca (`10107`), Cantón Central de San José, sobre el interfluvio confinado entre el **río Virilla** (norte) y el **río Torres** (sur), con ~61.0 ha operativas en geometría vectorial (`EPSG:5367` → `EPSG:4326`).
- **Malla microterritorial de 20 m:** **2,470 hexágonos regulares** (20 m entre vértices opuestos) recortados al perímetro de estudio en los **9 sectores comunales** (*María Auxiliadora, Central, Roble Norte, Pequeña Gran Ciudad, Las Brisas, Prodesarrollo, La Libertad, Roble Sur y San Vicente*).
- **Población modelada:** **30,252 habitantes** distribuidos de forma entera mediante mayores restos a partir de **5,460 viviendas estimadas** con Google Open Buildings v3 calibrado con levantamiento local de techos (ratio `0.988`).

### Línea base demográfica y habitacional distrital (INEC 2011 y 2022)

Como marco comparativo oficial documentado en `docs/censo-uruca-linea-base.md`, se incorpora la caracterización intercensal del **distrito de Uruca (código INEC `10107`)** según el Instituto Nacional de Estadística y Censos (INEC):

- **Censo Nacional 2011 (X de Población y VI de Vivienda):** **31,728 habitantes** y **8,389 viviendas individuales ocupadas**, con un promedio de **3.8 personas por vivienda** (superior al 3.5 cantonal y nacional).
- **Censo / Estimación 2022 (XI de Población y VII de Vivienda):** **43,484 habitantes** (+37.1% intercensal) y un promedio estimado de **~3.3 a 3.5 personas por vivienda** frente a **3.1** a nivel cantonal y nacional, confirmando la mayor densidad habitacional relativa en Uruca y sustentando el uso de factores calibrados específicos (4.5 hab/viv base y escenario de planificación de 5.4 hab/viv = 30,252 hab) dentro de La Carpio.

## Síntesis de resultados en el Geovisor y Tablero de Riesgo

1. **Población en condición Muy Alta / protección fluvial:** **4,687 habitantes (15.49%)** en **588 hexágonos de 20 m**, incorporando las zonas de protección de los ríos Virilla y Torres (Ley Forestal 7575) con puntaje máximo (100).
2. **Combinación de condicionantes de desarrollo (`1,523` hexágonos · `17,529` hab):** **12,779 hab (42.24%)** en deslizamiento alto/muy alto (`CATEGORIA_` 4–5), **4,475 hab (14.79%)** en solape de protección fluvial + deslizamiento alto/muy alto, y **212 hab (0.70%)** únicamente en protección de río, frente a **12,786 hab (42.26%)** sin intersección identificada en la plataforma central.
3. **Catálogo depurado en el Geovisor (`/aplicacion/`):** 7 capas temáticas solicitadas por el equipo técnico más el tablero estadístico de exposición poblacional bajo el mapa, complementados con el cuaderno reproducible `src/score_multiamenaza_edificaciones.ipynb` (v1.1).
