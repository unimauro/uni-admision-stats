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

## Pendiente
- [ ] **Proceso 2026-2 cerrado** (resultados finales publicados 15-ago): bajar la frecuencia del cron de uniexamen (hoy cada 12 h).
- [ ] Verificar visualmente la sección "Resultados finales" en el sitio publicado (desplegado sin revisión en navegador).
- [ ] Refrescar snapshot CAS de SalariosPerú y regenerar mercado laboral.
- [ ] (Menor) `salarioDe` empareja por substring — revisar casos borde; hoy muestra la carrera CAS emparejada en el tile.
- [ ] (Menor) Especialidades con 1 ingresante publican min=max=puntaje individual; la fuente UNI ya es pública, pero evaluar umbral de n.
