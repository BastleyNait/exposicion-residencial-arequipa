# Exposición Residencial Arequipa

Investigación aplicada y definición de producto sobre la **imposibilidad de verificar, antes de pagar, el estado legal‑urbanístico, de servicios y de peligro de una ubicación residencial en Arequipa, Perú.**

Repositorio de trabajo para el curso de Gestión de Sistemas y Tecnologías de Información.

---

## Tesis del repositorio

> El problema no es la ausencia de datos. Es que **el Estado organiza la información por institución y el ciudadano la necesita organizada por predio.**

Cinco capas de información existen y son públicas. Ninguna está integrada a nivel de ubicación, y ninguna está orientada a la decisión residencial.

---

## Estructura

| Ruta | Contenido |
|---|---|
| [`MEGA-DOCUMENTO.md`](MEGA-DOCUMENTO.md) | Documento único consolidado. Punto de entrada recomendado. |
| [`docs/00-evaluacion/`](docs/00-evaluacion/) | Evaluación metodológica: causa raíz, dossier de evidencia, ajuste solución‑mercado, **[referencias académicas Q1–Q4](docs/00-evaluacion/04-referencias-academicas.md)** |
| [`docs/01-verticales/`](docs/01-verticales/) | Análisis de los 6 verticales de información predial |
| [`docs/02-paises/`](docs/02-paises/) | Benchmark internacional, un archivo por país |
| [`docs/03-region/`](docs/03-region/) | Situación de Perú y de la región Arequipa |
| [`docs/04-startups/`](docs/04-startups/) | Panorama competitivo, con auditoría verificada de UbicaBien |
| [`docs/05-producto/`](docs/05-producto/) | Definición de producto y **[función clave: índice de incidencia](docs/05-producto/03-funcion-clave-indice-incidencia.md)** |
| [`data/fuentes.csv`](data/fuentes.csv) | Catálogo de fuentes de datos con formato, acceso y viabilidad técnica |
| [`referencias/pdf/`](referencias/pdf/) | **7 artículos y reportes descargados** (INEI, MININTER, PLOS ONE, Regional Science and Urban Economics, Springer) |
| [`slides/index.html`](slides/index.html) | Presentación ejecutiva (abrir en navegador) |

---

## Los seis verticales

| # | Vertical | Fuente principal en Perú | Estado digital |
|---|---|---|---|
| 1 | Legal / registral | SUNARP — Visor BGR, SPRL | Digital y georreferenciado |
| 1b | Catastral | **SNCP** (SUNARP preside, COFOPRI es Secretaría Técnica) | Código Único Catastral, cobertura por verificar |
| 2 | Urbanístico | Municipalidades (PDM, zonificación) | PDF por municipalidad |
| 3 | Peligro físico | SIGRID — CENEPRED, ANA | Digital, visor público |
| 4 | Servicios básicos | SEDAPAR, SEAL — proxy vía INEI 2017 | Presencial; proxy digital viable |
| **5** | **Exposición delictiva — función clave** | MININTER + reportes ciudadanos, calibrado con INEI/UCSP | Índice propio con semáforo — [especificación completa](docs/05-producto/03-funcion-clave-indice-incidencia.md) |
| 6 | Derechos mineros | INGEMMET | GeoJSON público (adoptado tras auditar a UbicaBien) |

---

## Hallazgo central del benchmark

En el mundo el problema se resuelve con **tres modelos**, y el Perú no tiene ninguno completo:

1. **Obligación legal de divulgación** — Reino Unido, Victoria (Australia), California
2. **Transferencia de riesgo vía seguro** — Estados Unidos
3. **Bien público digital** — Países Bajos, España, Estonia

Detalle en [`docs/02-paises/`](docs/02-paises/).

---

## Estado del trabajo

- [x] Definición y validación metodológica del problema
- [x] Benchmark internacional por país
- [x] Diagnóstico de fuentes de datos en Arequipa
- [x] Panorama competitivo
- [x] Definición de producto y plan de validación
- [x] Análisis del competidor directo — [UbicaBien](docs/04-startups/ubicabien.md), Arequipa
- [ ] Verificación de campo: naturaleza vectorial o raster del plano de zonificación de JLByR
- [ ] Verificación V1–V4: cobertura real de UbicaBien con su plan gratuito
- [ ] Entrevistas de desarrollo de clientes (n=15)
- [ ] Prueba de humo con umbral precomprometido

---

## Licencia

MIT. Las fuentes citadas conservan sus propios términos.
