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

## Pendiente
- [ ] **Física y Química** (3.ª prueba 2026-2): al 14-ago (18:15 UTC) AÚN NO publicada (verificado en fuente oficial y snapshot 17Z). El scraper la captará solo (cron 05/17 UTC). Frontend ya 100% listo para que aparezca sola: tiles fila principal, texto de sección dinámico, calculadora, top10 con nombres, histograma y ausentismo. Al llegar, solo verificar visualmente.
- [ ] **Resultados finales 2026-2** por especialidad: nueva sección de ingresantes + comparativa con 2026-1. Ojo esquema: solo ingresantes traerán `especialidad_ingreso`. Incluir ahí el **top por carrera** (hoy imposible: las publicaciones de examen solo traen código/nombres/puntaje, sin especialidad).
- [ ] Nota vigesimal del TOTAL 2026-2 (suma de 3 pruebas /1,800) cuando estén las 3.
- [ ] Comparar ausentismo final 2026-2 (3 pruebas) vs 2026-1.
- [ ] Al cerrar el proceso: bajar la frecuencia del cron.
- [ ] Refrescar snapshot CAS de SalariosPerú y regenerar mercado laboral.
- [ ] (Menor) `salarioDe` empareja por substring — revisar casos borde; hoy muestra la carrera CAS emparejada en el tile.
- [ ] (Menor) Especialidades con 1 ingresante publican min=max=puntaje individual; la fuente UNI ya es pública, pero evaluar umbral de n.
