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

Proyecto independiente, sin afiliación oficial con la UNI.
