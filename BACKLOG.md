# Backlog — uni-admision-stats

## Hecho
- [x] 2026-08-12 — Repo público; solo estadísticas agregadas, sin PII. Repos origen (uniexamen, uni-cepre) pasados a PRIVATE.
- [x] 2026-08-12 — Dashboard v1: examen 2026-2, CEPRE por especialidad, histórico 2026-1, monitoreo.
- [x] 2026-08-12 — Pipeline: `uniexamen` scrapea cada 12 h (GitHub Actions) y empuja `data/stats.json` vía deploy key.
- [x] 2026-08-12 — Sidebar, buscador de carrera, comparativas (sankey), mercado laboral CAS, FAQ, bot IA (ai.tunky), OG + favicon con escudo UNI, GA4, Yape + Buy Me a Coffee.
- [x] 2026-08-12 — Variación 2026-1 vs 2026-2, filtros por facultad, toggle claro/oscuro.
- [x] 2026-08-12 — Auditoría adversarial (15 hallazgos): corregidos colores de facultad (FIM/FIP), monitoreo mostraba solo 3 publicaciones, XSS escape, tooltip huérfano, rangePlot div-cero, salario CAS con match espurio, guards de calculadora, huecos en serie temporal. Bot resiste jailbreaks.
- [x] 2026-08-13 — **Escala de nota corregida**: examen 2026-2 = **600 pts por prueba** (1,800 total = nota 20), confirmado con Matemática (máx exacto 600). Ciclo 2026-1 usó 745+600+500=1,845. Nota vigesimal en TODAS las secciones (oficial en examen, referencial en CEPRE).
- [x] 2026-08-13 — **Segundo examen publicado**: Matemática (12 ago, 4,458 registros, máx 600, ausentismo 1.14%) auto-renderizado con tiles + histograma. También examen especial (47).
- [x] 2026-08-13 — **Top 10 por prueba 2026-2 con nombres**: una tarjeta por prueba (# / postulante / puntaje / nota, ordenadas por fecha, la última marcada "último examen"). Nombres tomados de la publicación oficial UNI (decisión del usuario); el scraper emite `top10` [{puntaje, nombre}] y la guardia anti-PII sigue bloqueando `nombres`/`codigo` (padrones crudos). En Matemática hubo DOS puntajes perfectos (600 = 20/20).
- [x] 2026-08-13 — **Tooltips explicativos en todos los tiles** (16): `tile()` acepta texto de ayuda, muestra ⓘ y usa el tooltip compartido (hover; en táctil, tap y se cierra tocando fuera). Incluye aria-label.

- [x] 2026-08-15 — **Física y Química publicada** (4,454 registros, máx 549): captada con scraper manual (el cron 05:30 UTC corrió antes de la publicación). Auto-render funcionó: tiles, histograma, top10, ausentismo, calculadora.
- [x] 2026-08-15 — **Resultados finales 2026-2**: la UNI publicó `resultados-concurso-admision-2026-2` (4,120 postulantes, 860 ingresantes) y `-arquitectura` (334/64) con **esquema nuevo**: `resultado` = especialidad de ingreso ('' = no ingresó), `modalidad`, y en Arquitectura `puntaje_final` + `puntaje_final_arquitectura` (/2,400 con vocacional). build_stats adaptado (`puntaje_de`, `especialidad_de`, `ingresantes`, `por_modalidad`).
- [x] 2026-08-15 — **Sección "Resultados finales" nueva**: tiles, TOP POR CARRERA (cierre y máximo /1,800 por especialidad), top 10 total con nombres, tabla Arquitectura/Urbanismo, comparativa de cierres 2026-2 vs 2026-1 en nota vigesimal, modalidades. Nav (sidebar + topnav), FAQ y textos de privacidad actualizados ("solo el top 10 oficial lleva nombre").
- [x] 2026-08-15 — **Bot con inteligencia actualizada**: contexto ampliado con las 3 pruebas, resultados finales (cierres altos/bajos, modalidades, 1eros puestos), Arquitectura/Urbanismo y la escala /1,800.

- [x] 2026-08-15 — **Ausentes de Física y Química**: la publicación no usa la marca AUSENTE; los ausentes figuran con 0,000 (161 ceros exactos = 3.61%, calza con el patrón del día 3 en 2026-1: 2.98%). build_stats los cuenta como ausentes solo cuando el padrón no trae ninguna marca AUSENTE (hipótesis del usuario, verificada contra las otras pruebas que sí marcan y no tienen ceros).
- [x] 2026-08-15 — **Confeti de celebración** al ver la sección Resultados finales (una vez por visita, respeta prefers-reduced-motion) + felicitación a los ingresantes en la nota.
- [x] 2026-08-15 — **Tablas visibles estilizadas** (`tablaBonita`): zebra, medallas 🥇🥈🥉, fila 1 resaltada, cabeceras uppercase, números tabulares, scroll horizontal. Aplicada a los Top 10 por prueba, Top 10 del concurso y Arquitectura/Urbanismo.

- [x] 2026-08-16 — **Notas mínimas y máximas por especialidad** (formato flyer UNI): `por_especialidad_ordinario` en el scraper (verificado contra el flyer oficial: solo modalidad ORDINARIO; Arquitectura /2,400). Tabla 2026-2 con facultad + código oficial (mapa ESP_COD) y tabla comparativa **2026-1 vs 2026-2 por carrera** (Δ mín; 2026-1 /1,845 con caveat de extraordinarias, Arq. /2,445 referencial). Top 10 del concurso ahora con columna Carrera (+carrera/modalidad en `top10` del stats.json). Bot sabe las notas mínimas oficiales.

## Pendiente
- [ ] **Datos abiertos históricos — investigación COMPLETA (17-ago), integración pendiente.** Hallazgos (URLs verificadas):
  - **1º CSV oficiales en datosabiertos.gob.pe** (microdato por postulante CON puntaje `CALIF_FINAL` + `INGRESO` + modalidad/sexo/departamento, ID hasheado, licencia ODC-BY): `Datos_abiertos_admision_2021_1_2024_1.csv` (13.2MB), `..._2024_2_2025_1_0.csv` (4.8MB), `..._2025_2_2026_1.csv` (3.5MB) en `https://www.datosabiertos.gob.pe/sites/default/files/`. Cobertura continua 2021-1→2026-1 (11 procesos). ⚠️ Escala cambia en 2025-2 (vigesimal → ~2000) y hay `CALIF_FINAL=0` que son ausentes. WAF exige User-Agent de navegador. API CKAN para detectar updates.
  - **2º 27 PDFs oficiales 2013-1→2025-2** (solo conteos por especialidad/modalidad/sexo, SIN puntajes): los enlaces vivos de admision.uni.edu.pe están TODOS 404; recuperables solo vía Wayback (`web.archive.org/web/<ts>id_/...`, rutas en informe). Archivar copia propia al extraer. `pdftotext -layout` funciona; PDFs viejos usan códigos A1/C1, nuevos FAUA/FIC.
  - 3º opcional: CSV CEPRE 2016-2023; DIRCE (form 2007-2→2026-1, requiere scraping navegador). TUNI/INEI descartados.
  - Gráficos posibles: serie postulantes/ingresantes desde 2013, ratio admisión por carrera (Civil 8.5% vs Textil 100% en 2025-1), brecha de género, modalidades, puntajes por carrera desde 2021, mapa por departamento.
- [ ] **Proceso 2026-2 cerrado** (resultados finales publicados 15-ago): bajar la frecuencia del cron de uniexamen (hoy cada 12 h).
- [ ] Verificar visualmente en navegador: sección "Resultados finales", tablas nuevas y confeti (desplegado sin revisión visual).
- [ ] Pregunta de usuarios (Diego): "tardanzas" no se publican, solo ausencias; el dato ya está en la tarjeta Ausentismo por prueba.
- [ ] Refrescar snapshot CAS de SalariosPerú y regenerar mercado laboral.
- [ ] (Menor) `salarioDe` empareja por substring — revisar casos borde; hoy muestra la carrera CAS emparejada en el tile.
- [ ] (Menor) Especialidades con 1 ingresante publican min=max=puntaje individual; la fuente UNI ya es pública, pero evaluar umbral de n.
