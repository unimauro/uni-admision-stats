# Admisión UNI en cifras

Dashboard público con estadísticas **agregadas y anónimas** de los procesos de admisión de la
Universidad Nacional de Ingeniería (UNI, Perú): postulantes, ausentismo y puntajes por prueba,
especialidad y modalidad.

**Dashboard:** https://unimauro.github.io/uni-admision-stats/

## Qué contiene

- `index.html` — dashboard estático (sin dependencias externas).
- `data/stats.json` — estadísticas agregadas generadas automáticamente.

## Qué NO contiene

Este repositorio **no contiene datos personales**: ni nombres, ni códigos de postulante,
ni ningún registro individual. Solo conteos, porcentajes, histogramas y resúmenes
estadísticos (mínimo, máximo, media, mediana, percentiles).

## Fuente y actualización

- Fuente: [publicaciones oficiales de la Dirección de Admisión UNI](https://puntajes.admision.uni.edu.pe/).
- Los datos se verifican automáticamente cada 12 horas durante el proceso de admisión;
  `data/stats.json` se actualiza desde un pipeline privado que descarga, archiva y agrega
  las publicaciones oficiales.

## Ecosistema

Este dashboard forma parte de un conjunto de proyectos ciudadanos de datos abiertos sobre la UNI,
del mismo autor y enlazados entre sí:

- [Observatorio UNI](https://unimauro.github.io/observatorio-uni/) — presupuesto y ejecución, proveedores,
  planilla, investigación y una sección de admisión que reutiliza estas estadísticas.
- [Observatorio Electoral UNI](https://unimauro.github.io/observatorio-electoral-uni/#/) — elección de
  rector y vicerrectores 2026: candidatos, fuentes, resultados y segunda vuelta.
- Admisión UNI en cifras (este repositorio).

Proyecto independiente, sin afiliación oficial con la UNI.
