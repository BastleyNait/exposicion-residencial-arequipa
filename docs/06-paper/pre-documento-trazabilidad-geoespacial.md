# Pre-documento de investigación: trazabilidad geoespacial de incidentes y debida diligencia inmobiliaria en Arequipa

**Versión:** 0.1, 29 de septiembre de 2026
**Estado:** protocolo y anteproyecto; **no** comunica resultados empíricos ni un sistema ya desplegado.
**Ámbito inicial:** vivienda y terrenos residenciales en Arequipa Metropolitana, con piloto propuesto en José Luis Bustamante y Rivero (JLByR).
**Base documental:** [Exposición Residencial Arequipa](https://github.com/BastleyNait/exposicion-residencial-arequipa) y [GSTI](https://github.com/BastleyNait/GSTI).

## 1. Título, resumen y aporte

**Título tentativo.** *Modelo auditable de trazabilidad geoespacial de incidentes delictivos y condiciones prediales para apoyar la compraventa residencial en Arequipa, Perú*.

**Resumen preliminar (propuesta, 180 palabras).** La información relevante para adquirir un inmueble en Arequipa está fragmentada entre registros prediales, planificación urbana, servicios, peligros físicos y seguridad ciudadana. Este estudio propone un sistema de apoyo a la decisión que vincule cada afirmación mostrada sobre un inmueble o su entorno con la fuente, fecha, resolución espacial, transformación y nivel de incertidumbre que la produjo. El componente prioritario es la exposición a delitos específicos —no una etiqueta genérica de «zona peligrosa»—, diferenciando denuncias oficiales, encuestas de victimización y reportes ciudadanos. La metodología prevé una auditoría de disponibilidad de datos, un prototipo espacial reproducible, una evaluación de calidad de geocodificación, análisis de sensibilidad y una prueba con compradores y especialistas. La salida prevista es un informe de debida diligencia que indique hallazgos, evidencia, límites y verificaciones pendientes; no un certificado legal ni una predicción infalible de victimización o precio. La hipótesis es que la trazabilidad mejora la comprensión de riesgos y la calidad de la decisión de compra respecto de consultar mapas y portales aislados. Cualquier relación con precio o velocidad de venta será una hipótesis secundaria y solo se estimará si se obtienen transacciones comparables.

**Palabras clave:** procedencia de datos; SIG; seguridad ciudadana; cifra negra; debida diligencia; vivienda; Arequipa; incertidumbre espacial.

**Aporte científico propuesto:** no «otro mapa de delitos», sino (i) una cadena verificable de evidencia desde incidente/fuente hasta afirmación predial, (ii) un método que evita convertir ausencia de datos en ausencia de riesgo, (iii) una evaluación explícita de la resolución espacial y del subregistro, y (iv) medición del efecto de esa transparencia sobre decisiones de compra. El aporte deberá demostrarse mediante comparación experimental; por ahora es una proposición.

## 2. Punto de partida y evidencia disponible

Los repositorios aportan un diagnóstico de seis verticales (registral, catastral, urbanístico, peligro, servicios, exposición delictiva y derechos mineros; registral/catastral se distinguen en la documentación), un catálogo de fuentes y un [índice de incidencia **especificado**](https://github.com/BastleyNait/exposicion-residencial-arequipa/blob/main/docs/05-producto/03-funcion-clave-indice-incidencia.md). GSTI añade una [exploración de servicios GIS](https://github.com/BastleyNait/GSTI/blob/main/docs/05-producto/04-servicios-gis-datos-abiertos.md) y una [especificación de interfaz](https://github.com/BastleyNait/GSTI/blob/main/docs/05-producto/05-especificacion-ui-mapa-consolidado.md). Son **documentos de diseño**: no se identificó un backend, un pipeline ejecutable, un conjunto de incidentes geocodificados listo para análisis, pruebas de exactitud o estimaciones de precio. La replicación posterior debe fijar el commit de ambos repositorios y la versión de cada dataset.

La necesidad social tiene respaldo, pero no valida el producto por sí sola. Según [INEI, *Victimización en el Perú 2025*](https://www.inei.gob.pe/media/MenuRecursivo/publicaciones_digitales/Est/Lib2076/libro.pdf), 33,5 % de la población urbana de 15 años o más de Arequipa declaró haber sido víctima de algún hecho delictivo en 2025; 15,0 % declaró más de un hecho. A escala nacional urbana, solo 19,5 % de las personas victimizadas declaró haber denunciado. **No** debe trasladarse ese 19,5 % directamente a cada delito, distrito, manzana o inmueble de Arequipa. Además, desde 2024 el indicador incorpora tentativas de extorsión: las comparaciones históricas requieren cautela.

El [Mapa del Delito de MININTER](https://www.gob.pe/33281-conocer-los-lugares-donde-se-han-denunciado-delitos-e-incidencias-mapa-del-delito) anuncia visualización de denuncias georreferenciadas; el [dataset abierto SIDPOL](https://www.datosabiertos.gob.pe/dataset/denuncias-policiales-1) se describe como desagregado por año, mes, departamento y tipo de hecho. **Ver el punto en un visor no prueba que exista descarga/API abierta de microdatos con coordenadas, autorización de reutilización ni precisión apta para publicar una manzana.** Esa viabilidad es el primer hito de investigación, no una premisa.

En el frente predial, [SUNARP explica que el CRI](https://www.gob.pe/institucion/sunarp/pages/26681-solicitar-certificado-registral-inmobiliario-cri) informa descripción, titularidad, cargas, gravámenes y títulos pendientes; requiere trámite y pago. Un mapa o ficha del prototipo no sustituirá ese documento ni la revisión notarial. [SIGRID/CENEPRED](https://sigrid4.cenepred.gob.pe/sigridv4/login) y el [servicio de catastro minero de INGEMMET](https://geocatmin.ingemmet.gob.pe/arcgis/rest/services/SERV_CATASTRO_MINERO_WGS84/MapServer) son fuentes adicionales de contexto territorial, con sus propias vigencias y límites de interpretación.

## 3. Problema y preguntas de investigación

**Problema central.** Un comprador debe integrar fuentes heterogéneas que responden a unidades distintas (partida, predio, lote, manzana, distrito), periodos distintos y grados de certeza distintos. La interfaz habitual oculta esas diferencias; por ejemplo, un punto delictivo, una tasa distrital y un dato registral pueden aparecer como si describieran el mismo inmueble con igual precisión.

**Pregunta principal:** ¿un informe predial con trazabilidad geoespacial y comunicación explícita de incertidumbre mejora la calidad de la debida diligencia de compradores residenciales frente a la consulta fragmentada de fuentes?

**Subpreguntas:**

1. ¿Qué fuentes pueden vincularse legal y técnicamente a una unidad predial o de vecindario, y con qué cobertura, latencia y error posicional?
2. ¿Qué categorías delictivas permiten inferencias útiles para seguridad residencial y cuáles no, dadas las diferencias entre lugar del hecho, lugar de denuncia, subregistro y población expuesta?
3. ¿Cómo cambia la clasificación de una zona al variar escala, ventana temporal, tasa, suavizado y fuente?
4. ¿Cuántas afirmaciones del reporte puede reconstruir un auditor a partir de evidencia primaria, versión de reglas y geometría usada?
5. ¿Los usuarios identifican mejor una oferta con señales registrales/urbanísticas contradictorias y evitan una decisión precipitada? ¿A qué costo de tiempo y comprensión?
6. Solo con datos de transacciones: ¿se asocia la exposición delictiva con precio de cierre, controlando atributos del predio, localización, tiempo y endogeneidad? Esta pregunta **no** es equivalente a demostrar que el sistema eleva precios o acelera ventas.

## 4. Objetivos, hipótesis y límites

**Objetivo general:** diseñar y evaluar un modelo reproducible de trazabilidad geoespacial de hechos delictivos y condiciones prediales para apoyar la compraventa residencial en Arequipa.

**Objetivos específicos:** (O1) auditar permisos, cobertura y calidad de fuentes; (O2) definir entidades, versiones y reglas de vinculación espacial; (O3) implementar un prototipo y un reporte explicable; (O4) validar exactitud y sensibilidad del componente delictivo; (O5) medir utilidad, comprensión y posibles daños informativos.

**H1 (auditabilidad):** el porcentaje de afirmaciones reproducibles desde fuentes primarias será mayor en el prototipo que en un reporte comparador sin linaje explícito.
**H2 (decisión):** los participantes con reporte trazable detectarán más incompatibilidades relevantes antes de elegir un inmueble, sin aumento inaceptable del tiempo de decisión.
**H3 (calibración):** una salida con estado «datos insuficientes» y rango de incertidumbre producirá menos confianza injustificada que un semáforo único.
**H4 exploratoria:** algunos delitos cercanos podrían asociarse con precio de transacción, pero magnitud y dirección dependen del contexto; **no se predefine un premio inmobiliario ni causalidad**. La literatura reporta heterogeneidad por tipo de delito y problemas de endogeneidad ([Ihlanfeldt y Mayock](https://www.sciencedirect.com/science/article/pii/S0166046210000086); [Wilhelmsson y Ceccato](https://www.sciencedirect.com/science/article/abs/pii/S0743016715000431)).

**No objetivos:** certificar titularidad o habilitación, estimar «valor verdadero» a partir de anuncios, predecir delitos individuales, nombrar víctimas/sospechosos, declarar que una propiedad es «segura» o prometer maximizar el precio de venta. «Mejorar compraventa» significa **reducir asimetría de información y errores evitables de decisión**, sujeto a evaluación.

## 5. Unidad de análisis y modelo conceptual

Se separan cuatro unidades: **predio** (geometría y/o partida verificada), **oferta** (anuncio cambiante, no prueba de dominio), **zona de seguridad** (polígono agregado que rodea la oferta) y **hecho/observación** (registro de una fuente con fecha y localización incierta). Un mismo punto de oferta puede corresponder a múltiples partidas o a ninguna geometría catastral disponible. Nunca se fuerza una relación 1:1.

Entidad mínima: `Predio(id_interno, geometria, fuente_geometria, precision, fecha_validacion)`; `Oferta(id, punto_declarado, fecha, precio_pedido, tipo, area, origen)`; `Fuente(id, autoridad, URL, licencia, frecuencia, unidad, granularidad, acceso)`; `VersionFuente(id, fecha_corte, fecha_descarga, checksum, esquema)`; `Observacion(id_fuente, id_original, categoria, tiempo_evento, tiempo_registro, geometria_o_zona, error_posicional, estado_verificacion)`; `VinculoEspacial(origen, destino, regla, distancia, porcentaje_interseccion, CRS, version_geometria)`; `Indicador(zona, periodo, categoria, numerador, denominador, metodo, intervalo, estado)`; `Afirmacion(reporte, texto, indicador_o_observacion, regla, version, advertencia)`.

La procedencia se puede expresar como grafo de **entidades → actividades → agentes** (modelo [W3C PROV](https://www.w3.org/TR/prov-o/)); un catálogo de activos geoespaciales puede apoyarse en [STAC](https://www.ogc.org/standards/stac/) si el volumen de archivos lo justifica. Para consulta interoperable de entidades espaciales, [OGC API – Features](https://www.ogc.org/standards/ogcapi-features/) es una opción, no un requisito para el piloto. Estas son **elecciones de diseño propuestas**, no tecnologías ya implementadas en los repositorios.

## 6. Cadena de trazabilidad detallada

Cada resultado del reporte debe poder seguir esta secuencia, de ida y vuelta:

`Autoridad / productor → publicación original → versión capturada + hash → permisos y cobertura → validación de esquema → normalización de fechas/categorías/CRS → geocodificación y error → deduplicación → agregación espacial y temporal → denominador y ajuste de subregistro (si procede) → cálculo + versión de reglas → prueba de sensibilidad → afirmación en reporte → consulta de auditoría`.

**Campos obligatorios por eslabón:** identificador persistente; URL y responsable; fecha del fenómeno, de registro, de publicación y de descarga **por separado**; licencia/permiso; cobertura espacial y temporal; granularidad; sistema de coordenadas; precisión original y transformada; versión de catálogo de delitos; código/regla y commit; parámetros; checksum de entrada y salida; número de registros aceptados/rechazados; motivo de rechazo; revisor; fecha de expiración; estado público (`verificado`, `estimado`, `referencial`, `desactualizado`, `insuficiente`, `no disponible`).

| Etapa | Evidencia que se preserva | Regla de control | Fallo que evita |
|---|---|---|---|
| Captura | URL/archivo original, licencia, hash, fecha de corte | No sobreescribir versiones | Imposibilidad de reproducir un resultado pasado |
| Semántica | Diccionario y correspondencia de categorías | Separar delito, falta, incidente y percepción | Sumar fenómenos no equivalentes |
| Geocodificación | Texto/punto original protegido, método, confianza, distancia de ajuste | Rechazar dirección de comisaría como lugar del hecho salvo verificación | Hotspots ficticios en comisarías |
| Tiempo | Fecha del hecho y de denuncia, zona horaria, ventana | Alinear periodos; evitar usar datos posteriores a la consulta | Fuga temporal y tendencia falsa |
| Espacio | Geometría fuente, CRS, tolerancia, versión de límites | Usar incertidumbre de ubicación; no atribuir a manzana sin soporte | Falsa precisión predial |
| Duplicados | IDs fuente y huellas probabilísticas protegidas | Marcar coincidencia, no fusionar sin evidencia | Inflar conteos por múltiples canales |
| Agregación | Numerador, población/exposición, área, método y supresión | Umbral de privacidad; tasa y conteo visibles | Inferencia sobre individuos o tasa inestable |
| Resultado | Script, parámetros, intervalos, semilla, pruebas | Reejecutar desde snapshot | Índice opaco o irreproducible |
| Publicación | Claim ID enlazado a evidencias, límites y vigencia | Auditoría de «por qué aparece esto» | Confundir evidencia con certificación |

**Ejemplo ilustrativo, no dato real.** Una oferta cae en una zona `Z-14`. El reporte afirma «se registraron denuncias de robo en el entorno durante los 12 meses previos a la consulta». El enlace de auditoría devuelve: corte SIDPOL, ID del lote y hash; definición exacta de robo; conteo elegible y descartado; porcentaje geocodificado; geometría de `Z-14`; población/exposición usada; fecha de ejecución y versión del algoritmo; rango de incertidumbre; advertencia de subregistro. Si solo existe una tabla distrital, la afirmación cambia a «dato distrital» y **no** se muestra como incidencia de `Z-14` ni como rasgo del predio.

La trazabilidad también comprende correcciones: un dato fuente rectificado crea nueva versión, invalida indicadores dependientes, conserva el reporte histórico emitido y ofrece un reporte actualizado con diferencias explicadas. Una apelación sobre ubicación errónea debe tener canal humano, registro de decisión y plazo de revisión. No publicar detalles que permitan inferir identidad de víctimas.

## 7. Diseño del componente delictivo: de hechos específicos a contexto residencial

### 7.1 Taxonomía

Primer nivel: robo/hurto de vivienda, robo con violencia en vía pública, hurto en vía pública, robo de vehículo, extorsión, daños a propiedad y otros hechos si fuente y tamaño muestral lo permiten. Cada tipo tendrá código fuente, regla de agrupación, unidad de exposición y posible relevancia residencial. **No** se funden denuncias de violencia doméstica o sexual en mapas prediales de acceso público: su localización puede revelar víctimas; para estos fenómenos se usan, si son pertinentes, solo estadísticas suficientemente agregadas y aprobadas éticamente. «Daños específicos» puede ampliarse a perjuicios materiales y peligros físicos, pero deben permanecer en capas conceptualmente separadas de delincuencia.

### 7.2 Fuentes y denominadores

1. **Denuncias policiales:** hechos registrados, no total de delitos ocurridos. Auditar si hay microdatos geocodificados legalmente utilizables; no extraer masivamente el visor sin autorización documentada.
2. **INEI/ENAPRES:** estimación muestral de victimización y denuncia, adecuada para calibración/contexto en el nivel publicado; no convertir directamente la tasa departamental en factor manzana. En 2025 la denuncia nacional entre victimizados fue 19,5 %, y para robo en vivienda el informe reporta 21,1 % entre viviendas afectadas: son poblaciones y métricas diferentes ([INEI 2025](https://www.inei.gob.pe/media/MenuRecursivo/publicaciones_digitales/Est/Lib2076/libro.pdf)).
3. **Reportes ciudadanos:** estudio piloto optativo, separado de denuncias, con consentimiento, verificación y control de duplicados. Un reporte no probado **no** equivale a un delito confirmado ni se usa automáticamente para calificar una zona.
4. **Exposición:** habitantes, hogares, viviendas, flujo peatonal o vehículos según delito y disponibilidad. «Tasa por 10 000 habitantes» no es denominador universal para robo a vivienda o a vehículo. Cuando no haya denominador congruente, publicar conteo contextual con advertencia, no una tasa engañosa.

### 7.3 Métrica provisional y regla de no publicación

Para delito `k`, zona `z` y ventana `t`: `r[k,z,t] = n[k,z,t] / e[k,z,t] × escala`, donde `n` son hechos elegibles y `e` es la población/exposición apropiada. Mostrar conteo, denominador, periodo, geocodificación y un intervalo de incertidumbre. Comparar con zonas pares solo si las tasas son comparables y el tamaño es suficiente. Para conteos pequeños, evaluar suavizado empírico bayesiano **con validación y transparencia**; no esconder el dato crudo.

Estado **gris / evidencia insuficiente** cuando no existe acceso válido, cobertura espacial, denominador, ventana congruente, precisión o tamaño adecuados. Los umbrales mínimos se pre-registrarán con expertos en estadística, seguridad y privacidad tras inspección de datos; no se inventan aquí. «Cero denuncias» y «sin datos» son estados distintos.

La fórmula `D_corregida^0,6 × R_ciudadana^0,4` del [documento de producto](https://github.com/BastleyNait/exposicion-residencial-arequipa/blob/main/docs/05-producto/03-funcion-clave-indice-incidencia.md) es **hipótesis de diseño, no índice validado**. Presenta tres problemas antes de aplicarla: (a) si `R_ciudadana=0`, el producto vale cero aunque `D_corregida>0`; (b) las tasas no están normalizadas y calibradas a `[0,1]` antes de aplicar bandas de ese rango; (c) la razón victimización/denuncias puede mezclar personas, hechos, categorías, poblaciones y periodos. No se usarán bandas «oficiales del INEI» para el nuevo índice sin derivación y validación propias. En el piloto se compararán un **tablero de indicadores separados** (preferencia inicial por honestidad) y, solo si supera pruebas de estabilidad/calibración, un compuesto con pesos estimados o acordados de antemano. Ningún 0,6/0,4 se defenderá como resultado empírico local sin evidencia.

### 7.4 Sensibilidad, sesgo y geografía

Estimar qué porcentaje se geocodifica por distrito y tipo; comparar incluidos/excluidos; verificar cambios al usar polígonos alternativos, radios, distancias por red, ventanas de 6/12/24 meses y diferentes denominadores. La unidad de análisis no debe elegirse después de ver los hotspots. Usar cortes temporales y validación espacial fuera de muestra para cualquier modelo predictivo; no dividir aleatoriamente puntos vecinos y declarar generalización. Comunicar el **problema de unidad espacial modificable**: una manzana «roja» puede pasar a «verde» al cambiar límites o ventana. La distribución de denuncias depende tanto de delito como de propensión a denunciar y presencia policial.

## 8. Conexión con la compraventa inmobiliaria

**Flujo del comprador:** (1) ingresar dirección, coordenada u oferta; (2) confirmar localización y correspondencia predial, o marcar incertidumbre; (3) visualizar una matriz de seis capas con estado y fecha; (4) abrir evidencias y contradicciones; (5) descargar checklist de diligencias; (6) solicitar CRI/consulta profesional; (7) comparar inmuebles con la **misma fecha y metodología**. La pantalla debe distinguir «incidencia en entorno» de «hecho en el inmueble». El vendedor puede aportar documentación, pero no editar hallazgos sin traza.

**Matriz mínima de decisión:**

| Dimensión | Pregunta para comprador | Evidencia posible | Límite explícito |
|---|---|---|---|
| Registral | ¿El vendedor puede transferir el bien? | CRI/partida y títulos pendientes, con fecha | Revisión profesional y vigencia; no certificar desde mapa |
| Catastral | ¿Coinciden ubicación y descripción? | Geometría/código disponible, levantamiento | Cobertura incompleta, superposiciones |
| Urbanística | ¿Uso y parámetros admiten lo previsto? | Plano/norma municipal vigente | PDF no georreferenciado exige revisión manual |
| Peligro físico | ¿Hay exposición a sismo, inundación, huaico? | SIGRID/estudios específicos | Escala y antigüedad del estudio |
| Servicios | ¿Hay conexión efectiva? | Certificación de proveedor; INEI como proxy | Cercanía a red ≠ factibilidad de conexión |
| Delincuencia | ¿Qué hechos se registraron en el entorno y con qué incertidumbre? | Fuente oficial/encuesta agregada | Subregistro y resolución espacial |
| Minería | ¿Existe superposición con derecho minero? | INGEMMET, consulta vigente | Superposición no implica automáticamente prohibición de venta o construcción |

El producto puede mejorar transparencia, reducir búsquedas y señalar diligencias pendientes; su efecto sobre precio de cierre, tiempo de venta, fraude evitado o satisfacción requiere **medición propia**. La literatura hedónica observa asociaciones entre crimen y vivienda en otros contextos, pero no autoriza trasplantar coeficientes a Arequipa ([Ihlanfeldt y Mayock](https://www.sciencedirect.com/science/article/pii/S0166046210000086)).

## 9. Metodología empírica y validación

**Diseño:** estudio aplicado de métodos mixtos en tres fases, con protocolo pre-registrado antes de analizar resultados. La fase 1 es una auditoría de fuentes y licencias; la fase 2, prototipo y validación técnica; la fase 3, evaluación con usuarios. La estimación econométrica de precio es un módulo condicional independiente.

**Fase 1 — factibilidad (puerta de decisión).** Inventariar los campos efectivos de cada fuente, su licencia, granularidad, coordenadas, periodo y modalidad de acceso; solicitar convenio/acceso si hace falta. Muestra de verificación manual estratificada por distrito y tipo de fuente para evaluar geocodificación y vigencia. Si no hay incidentes legalmente accesibles con posición suficientemente precisa, el paper pasa a **prototipo con datos agregados** y prueba de trazabilidad; no inventa microdatos ni dibuja hotspots puntuales. Verificar también el plano de zonificación de JLByR (vector/raster) y la correspondencia con predios.

**Fase 2 — validación técnica.** Construir *baseline* de mapa/tabla sin linaje, y prototipo trazable. Indicadores: completitud de metadatos, porcentaje de afirmaciones reconstruibles por auditor independiente, coincidencia espacial con puntos verificados, error mediano/percentiles de geocodificación, latencia de actualización, tasa de fallos y estabilidad de clasificación frente a parámetros. Mantener datos de prueba separados y registrar todas las transformaciones. Un tercero debe regenerar al menos una muestra de reportes usando snapshots, versión de código y parámetros publicados.

**Fase 3 — evaluación de decisión.** Reclutar compradores potenciales y profesionales inmobiliarios con criterios documentados. Asignar aleatoriamente escenarios equivalentes a reporte trazable o fuentes fragmentadas (orden contrabalanceado si cada participante usa ambos); medir detección de alertas predefinidas, decisiones justificadas, tiempo, carga cognitiva, confianza calibrada y utilidad percibida. Escenarios con «sin datos» son obligatorios. No medir únicamente preferencia estética. Definir tamaño muestral mediante piloto de varianza/efecto mínimo relevante y análisis de potencia, no un `n` arbitrario.

**Módulo de mercado, solo si hay datos:** transacciones **cerradas** con fecha, coordenada fiable, precio, área, tipología y atributos suficientes; evitar usar precio pedido como precio de venta. Estimar modelo hedónico espaciotemporal con efectos de zona/tiempo y controles, comparar delitos específicos y aplicar sensibilidad a vecindario y selección. Tratar endogeneidad y confusión; sin estrategia identificadora defendible, reportar asociación, no efecto causal. Separar estrictamente desempeño del sistema de asociación crimen-precio.

**Criterios de éxito propuestos, a pre-registrar antes del piloto:** reproducibilidad completa de afirmaciones publicadas en muestra auditada; mejora estadística y sustantivamente relevante en detección de alertas del experimento; ninguna divulgación de ubicación sensible; clasificación robusta bajo variaciones razonables de escala/ventana. Los valores numéricos finales deben acordarse con director del paper y datos preliminares, nunca escogerse después de ver resultados.

## 10. Riesgos, ética y cumplimiento

La divulgación de puntos delictivos exactos puede reidentificar víctimas, estigmatizar barrios, facilitar acoso o perjudicar vendedores sin base suficiente. La guía del [National Institute of Justice sobre privacidad de mapas delictivos](https://www.ojp.gov/pdffiles1/nij/188739.pdf) respalda tratar precisión y publicación como decisiones separadas. Aplicar minimización, control de acceso, agregación/supresión, retención limitada, bitácora de consultas y revisión ética. El uso de geolocalización y reportes ciudadanos debe evaluarse conforme a la [Ley peruana de protección de datos personales y su reglamento aprobado por D. S. 016-2024-JUS](https://www.gob.pe/institucion/anpd/normas-legales/6554453-n-016-2024-jus), con asesoría jurídica antes de operar.

No usar reportes no verificados como prueba de delito ni publicar nombres, narrativas libres, domicilios de víctimas o puntos exactos de hechos sensibles. Definir rectificación y apelación. Separar evidencia territorial de juicio moral sobre residentes. La interfaz debe indicar fecha y grado de incertidumbre junto al color: el gris no significa seguridad. La conclusión del paper incluirá cobertura desigual de datos y riesgo de sesgo socioespacial.

## 11. Plan de trabajo y entregables verificables

| Etapa | Trabajo | Entregable | Condición para avanzar |
|---|---|---|---|
| 1 | Auditoría bibliográfica y jurídica | Matriz de literatura, licencias y permisos | Fuentes primarias y uso permitido verificados |
| 2 | Auditoría de datos Arequipa | Diccionario, cobertura, muestra de calidad y factibilidad SIDPOL/visor | Resolución real documentada |
| 3 | Diseño reproducible | Modelo de datos, taxonomía, protocolo y pre-registro | Definiciones y pruebas aceptadas por asesor |
| 4 | Prototipo | ETL versionado, base espacial, API/reporte y bitácora PROV mínima | Reejecución de muestra desde snapshots |
| 5 | Evaluación técnica | Errores, sensibilidad, privacidad, auditoría independiente | Sin precisión falsa ni exposición sensible |
| 6 | Estudio de usuarios | Instrumentos, datos anonimizados y análisis | Consentimiento y potencia justificados |
| 7 | Paper | Métodos, resultados reales, limitaciones y materiales reproducibles | Separación inequívoca entre hallazgos y propuestas |

**Decisiones abiertas prioritarias:** acceso a incidentes por lugar del hecho; licencia y nivel publicable; unidad espacial válida; denominadores por delito; vectorización de zonificación; disponibilidad de transacciones cerradas; aprobación ética; revista/conferencia y estilo bibliográfico. Si falla la primera puerta de datos, el paper conserva valor como investigación de **trazabilidad y comunicación de incertidumbre** con agregados, pero renuncia a afirmar incidencia por manzana.

## 12. Estructura recomendada del manuscrito final

1. Introducción y contribución.
2. Antecedentes: cifra negra, geografía del delito, información predial y precios hedónicos.
3. Contexto de Arequipa y auditoría de fuentes.
4. Modelo de procedencia y vinculación espacial.
5. Diseño experimental y validación técnica.
6. Resultados observados (solo tras ejecutar el protocolo).
7. Discusión: sesgos, privacidad, generalización, utilidad para compraventa.
8. Conclusiones, disponibilidad de datos/código y trabajo futuro.

## 13. Referencias núcleo verificadas (selección)

- INEI (2026), [*Victimización en el Perú 2025*](https://www.inei.gob.pe/media/MenuRecursivo/publicaciones_digitales/Est/Lib2076/libro.pdf). Estadísticas de victimización, denuncia y robo en vivienda; leer ámbito y notas metodológicas.
- MININTER, [Mapa del Delito Georreferenciado](https://www.gob.pe/33281-conocer-los-lugares-donde-se-han-denunciado-delitos-e-incidencias-mapa-del-delito) y [Denuncias Policiales SIDPOL en Datos Abiertos](https://www.datosabiertos.gob.pe/dataset/denuncias-policiales-1). No presuponer microdatos públicos por existencia del visor.
- SUNARP, [Certificado Registral Inmobiliario](https://www.gob.pe/institucion/sunarp/pages/26681-solicitar-certificado-registral-inmobiliario-cri).
- CENEPRED, [SIGRID](https://sigrid4.cenepred.gob.pe/sigridv4/login); INGEMMET, [Catastro Minero WGS84](https://geocatmin.ingemmet.gob.pe/arcgis/rest/services/SERV_CATASTRO_MINERO_WGS84/MapServer).
- Ihlanfeldt, K. R. y Mayock, T. (2010), [“Panel data estimates of the effects of different types of crime on housing prices”](https://www.sciencedirect.com/science/article/pii/S0166046210000086). Heterogeneidad por delito y endogeneidad.
- Wilhelmsson, M. y Ceccato, V. (2015), [“Does burglary affect property prices in a nonmetropolitan municipality?”](https://www.sciencedirect.com/science/article/abs/pii/S0743016715000431). Sensibilidad al contexto y al periodo.
- W3C, [PROV-O](https://www.w3.org/TR/prov-o/); OGC, [STAC](https://www.ogc.org/standards/stac/) y [OGC API – Features](https://www.ogc.org/standards/ogcapi-features/). Estándares de procedencia, catálogo y consulta.
- National Institute of Justice, [*Privacy in the Information Age: A Guide for Sharing Crime Maps and Spatial Data*](https://www.ojp.gov/pdffiles1/nij/188739.pdf). Riesgos de publicación espacial.
- Autoridad Nacional de Protección de Datos Personales, [D. S. 016-2024-JUS](https://www.gob.pe/institucion/anpd/normas-legales/6554453-n-016-2024-jus).

> **Nota editorial:** Antes de enviar el paper, convertir esta selección a estilo APA/IEEE exigido, comprobar DOI, páginas y fecha de consulta, y añadir únicamente bibliografía efectivamente leída. Las referencias de los repositorios son insumos de investigación, no sustitutos de resultados replicados.
