# Backlog — uni-admision-stats

## Hecho
- [x] 2026-08-12 — Repo público creado; solo estadísticas agregadas, sin PII.
- [x] 2026-08-12 — Dashboard v1: examen 2026-2 (ausentismo, histogramas), CEPRE por especialidad (rango de puntajes), histórico 2026-1 (modalidades, cierre por especialidad), monitoreo de snapshots.
- [x] 2026-08-12 — Pipeline: repo privado `uniexamen` scrapea cada 12 h (GitHub Actions) y empuja `data/stats.json` aquí vía deploy key.

## Pendiente
- [ ] Cuando se publiquen Matemática y Física-Química (2026-2): verificar que aparezcan automáticamente en el dashboard.
- [ ] Cuando salgan resultados finales 2026-2: sección de ingresantes por especialidad y comparativa 2026-1 vs 2026-2.
- [ ] Comparar ausentismo final 2026-2 (3 días) contra 2026-1.
- [ ] Considerar dominio propio si el sitio gana tracción.

## Iteración 2 (12-ago-2026 tarde)
- [x] Sección "Variación 2026-1 → 2026-2" (prueba 1 y CEPRE vs CEPRE).
- [x] Filtros por facultad con colores (CEPRE vacantes + cierre 2026-1) y facultad en la ficha de carrera.
- [x] Calculadora de percentil + nota equivalente sobre 20 (referencial).
- [x] Toggle claro/oscuro persistente, escudo UNI en favicon/OG, GA4 (G-NMFHSDRJD6).
- [x] Link a SalariosPerú y bloque de apoyo (Yape QR + Buy Me a Coffee).
