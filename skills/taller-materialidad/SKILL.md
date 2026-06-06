---
name: taller-materialidad
description: >-
  Conduce un análisis de materialidad ESG completo de extremo a extremo (flujo
  M1 a M6) para una empresa: identificación de temas materiales candidatos por
  sector, consulta a stakeholders, construcción de la matriz de materialidad,
  doble materialidad ESRS opcional, mapeo a indicadores GRI/SASB y captura de
  datos. Úsala SIEMPRE que el usuario pida un análisis de materialidad, una
  matriz de materialidad, identificar temas materiales, una consulta a grupos de
  interés, o construir una batería de indicadores de sostenibilidad. Frases como
  "actualicemos la materialidad de X", "necesito la matriz de doble
  materialidad", "qué temas son materiales para este sector", o "armemos los
  indicadores" también activan esta skill.
---

# Taller de Materialidad (M1 → M6)

Este es el procedimiento canónico de Horizonte Sostenible para conducir un
análisis de materialidad. Es un flujo de seis etapas. No las saltes sin razón,
pero adáptate: si el cliente solo necesita hasta la matriz (M3), no fuerces M4-M6.

## Antes de empezar: confirma el contexto

No generes temas sin tener: **sector**, **industria específica**, **tamaño**,
**país/región de operación** y **estándar objetivo** (GRI 2021 / SASB / doble
materialidad ESRS). Si falta algo, pregúntalo. Confirma también el **propósito**:
¿reporte público, batería interna de indicadores, certificación?

Si el cliente ya hizo el diagnóstico ESG (102 preguntas), usa ese resultado para
pre-seleccionar temas: las dimensiones con brechas altas suelen contener temas
materiales.

---

## M1 — Identificación de temas materiales

Genera un universo de **25-30 temas candidatos**. Para cada tema:

- **nombre**: máx. 5 palabras
- **dimension**: "E" | "S" | "G"
- **descripcion**: una oración de por qué es relevante para ESTE sector específico
  (no genérico)
- **fuente**: "GRI 2021" | "SASB" | "ESRS" | "Regulación colombiana" | "Múltiple"
- **relevancia_sectorial**: "Alta" | "Media" | "Baja"
- **urgencia_regulatoria_colombia**: "Alta" | "Media" | "Baja"
- **codigo_estandar**: el código específico SOLO si lo verificas en las tablas de
  referencia incrustadas más abajo en este archivo (Tabla A y Tabla B). Si no está
  ahí, deja el campo como "por confirmar" y dilo. **Nunca inventes un código.**

**Presenta los temas en pantalla como una tabla legible en español** (ver sección
"Formato de salida y entregables" al final). Mantén internamente la estructura de
datos (JSON) para las etapas siguientes, pero no la muestres como respuesta
principal. Ofrece exportar a Excel; genera el archivo solo si te lo piden.

**Intervención humana obligatoria:** presenta los temas al cliente. Él selecciona
cuáles incluir y asigna a cada uno un **puntaje de impacto del negocio (1-5)**.
Luego cruzas ese puntaje con pesos sectoriales para obtener el eje Y de la matriz.

---

## M2 — Consulta a stakeholders

A partir de los temas seleccionados en M1, genera una **encuesta** donde los
grupos de interés puntúan la importancia de cada tema (1-5). Grupos típicos:
empleados, comunidad, clientes, inversionistas, reguladores. Pondera por grupo
según relevancia para la empresa.

Calcula el **promedio ponderado de importancia por tema** → este es el eje X.

**Atajo MVP:** si no hay encuesta digital, el consultor puede ingresar
manualmente los promedios de encuestas físicas o externas. Acéptalo.

---

## M3 — Matriz de materialidad

Construye las coordenadas de cada tema:
- **Eje X** = importancia para stakeholders (output M2)
- **Eje Y** = impacto del negocio (output M1 ponderado)

Clasifica cada tema en un cuadrante:
- **Alto material**: alto en ambos ejes
- **Material**: alto en uno
- **En seguimiento**: medio en ambos
- **No material**: bajo en ambos

Etiqueta cada punto por dimensión E/S/G. Presenta la matriz como una **tabla
legible** (tema, eje X, eje Y, cuadrante, dimensión) con una lectura en prosa de
qué significan los resultados para la empresa. Mantén las coordenadas como datos
estructurados internamente para graficar. Ofrece exportar a Excel (con gráfico de
dispersión si es posible); genera el archivo solo si te lo piden.

---

## M4 — Doble materialidad (ESRS) — solo si aplica

Ejecuta esta etapa SOLO si el estándar objetivo es ESRS / doble materialidad.

Evalúa el **impacto financiero potencial** de cada tema material (riesgo y
oportunidad financiera) y crúzalo con el impacto hacia afuera (M3) para construir
la matriz de doble materialidad. Clasifica según familias ESRS (E1-E5, S1-S4, G1).

**ADVERTENCIA OBLIGATORIA AL CLIENTE:** en el MVP esto es una *aproximación
metodológica*, no un ejercicio de doble materialidad auditable bajo CSRD. Dilo
explícitamente. No sobreprometas conformidad regulatoria europea.

---

## M5 — Matriz de indicadores GRI/SASB sugerida

Para cada tema material **validado**, mapea los indicadores **relevantes** (no
los 200 de GRI — solo los que aplican al tema y al sector). Apóyate primero en la
**Tabla A** (catálogo maestro temático, más abajo) para ubicar el estándar
correcto (ej. tema "gestión de residuos" → GRI 306 Residuos), y luego en la
**Tabla B** (disclosures finos) para el código exacto del disclosure. Para cada
indicador:

- nombre del indicador
- **código** (leído de la Tabla A o Tabla B incrustadas en este archivo)
- descripción
- unidad de medida
- frecuencia de reporte sugerida
- fuente de datos recomendada (de dónde sale el dato dentro de la empresa)

Cruza también con la **Tabla C** (regulación colombiana): si un tema está cubierto
por una norma colombiana (ej. CE 015/2025, Decreto 2046/2019 BIC), señálalo como
indicador con urgencia regulatoria, usando la columna "Preguntas conectadas" para
trazar el vínculo.

---

## M6 — Captura de datos

Diseña la interfaz/formato simple para que la empresa ingrese el dato de cada
indicador definido en M5. Tipos soportados: número, texto, porcentaje, fecha,
documento adjunto. Estos datos alimentan el informe de sostenibilidad final.

---

## REGLA DE ORO — códigos de estándar

Los códigos GRI/SASB/ISSB/ESRS solo se toman de las tablas de referencia
verificadas que están **incrustadas más abajo en este mismo archivo**. No dependen
de archivos externos: están aquí, en el SKILL.md, siempre disponibles cuando esta
skill se activa.

Si un código no está en estas tablas, **no lo inventes**. Di "el código exacto
debe confirmarse contra la versión vigente del marco". Un código falso en un
entregable destruye la credibilidad técnica de Horizonte. Más vale un "por
confirmar" honesto.

**Cobertura de temas en M1:** recorre el catálogo maestro temático (Tabla A) para
asegurar que consideraste todas las áreas GRI relevantes al sector antes de cerrar
la lista de candidatos. Recuerda que los temas materiales dependen del sector: usa
criterio para descartar los que no apliquen y justifica por qué (como exige GRI 3).

---

## Tabla A — Catálogo maestro de Estándares Temáticos GRI

Úsala en M1 (barrer universo de temas) y M5 (ubicar el estándar correcto).

| Serie | Código | Nombre oficial del estándar | Dimensión |
| --- | --- | --- | --- |
| Económica | GRI 201 | Desempeño económico | G |
| Económica | GRI 202 | Presencia en el mercado | S |
| Económica | GRI 203 | Impactos económicos indirectos | S |
| Económica | GRI 204 | Prácticas de adquisición | G |
| Económica | GRI 205 | Anticorrupción | G |
| Económica | GRI 206 | Competencia desleal | G |
| Económica | GRI 207 | Fiscalidad | G |
| Ambiental | GRI 301 | Materiales | E |
| Ambiental | GRI 302 | Energía | E |
| Ambiental | GRI 303 | Agua y efluentes | E |
| Ambiental | GRI 304 | Biodiversidad | E |
| Ambiental | GRI 305 | Emisiones | E |
| Ambiental | GRI 306 | Residuos | E |
| Ambiental | GRI 308 | Evaluación ambiental de proveedores | E |
| Social | GRI 401 | Empleo | S |
| Social | GRI 402 | Relaciones trabajador-empresa | S |
| Social | GRI 403 | Salud y seguridad en el trabajo | S |
| Social | GRI 404 | Formación y enseñanza | S |
| Social | GRI 405 | Diversidad e igualdad de oportunidades | S |
| Social | GRI 406 | No discriminación | S |
| Social | GRI 407 | Libertad de asociación y negociación colectiva | S |
| Social | GRI 408 | Trabajo infantil | S |
| Social | GRI 409 | Trabajo forzoso u obligatorio | S |
| Social | GRI 410 | Prácticas en materia de seguridad | S |
| Social | GRI 411 | Derechos de los pueblos indígenas | S |
| Social | GRI 413 | Comunidades locales | S |
| Social | GRI 414 | Evaluación social de proveedores | S |
| Social | GRI 415 | Política pública | G |
| Social | GRI 416 | Salud y seguridad de los clientes | S |
| Social | GRI 417 | Marketing y etiquetado | S |
| Social | GRI 418 | Privacidad del cliente | S |

---

## Tabla B — Disclosures verificados (códigos finos GRI/SASB/ISSB/BIC)

Úsala en M5 para el código exacto de cada indicador. Validada por Horizonte Sostenible.

| Marco | Código | Tema / Disclosure | Comentario |
| --- | --- | --- | --- |
| GRI | 2-3 | Periodo del reporte y contacto | Universal Standard |
| GRI | 2-4 | Reformulación de información | Universal Standard |
| GRI | 2-5 | Verificación externa | Universal Standard |
| GRI | 2-7 | Empleados | Universal Standard |
| GRI | 2-9 | Estructura de gobierno y composición | Universal Standard |
| GRI | 2-12 | Rol del máximo órgano en supervisión de impactos | Universal Standard |
| GRI | 2-13 | Delegación de responsabilidad sobre impactos | Universal Standard |
| GRI | 2-14 | Rol del máximo órgano en informe de sostenibilidad | Universal Standard |
| GRI | 2-19 | Políticas de remuneración | Universal Standard |
| GRI | 2-20 | Proceso para determinar la remuneración | Universal Standard |
| GRI | 2-22 | Declaración sobre estrategia de desarrollo sostenible | Universal Standard |
| GRI | 2-23 | Compromisos de política | Universal Standard |
| GRI | 2-24 | Incorporación de los compromisos de política | Universal Standard |
| GRI | 2-25 | Procesos para remediar impactos negativos | Universal Standard |
| GRI | 2-27 | Cumplimiento de leyes y regulaciones | Universal Standard |
| GRI | 2-28 | Membresías en asociaciones | Universal Standard |
| GRI | 2-29 | Enfoque para la participación de stakeholders | Universal Standard |
| GRI | 2-30 | Convenios colectivos | Universal Standard |
| GRI | 3-1 | Proceso para determinar temas materiales | Universal Standard |
| GRI | 3-2 | Lista de temas materiales | Universal Standard |
| GRI | 3-3 | Gestión de temas materiales | Universal Standard |
| GRI | 201-1 | Valor económico generado y distribuido | Topic Standard — Economic |
| GRI | 201-2 | Implicaciones financieras del cambio climático | Topic Standard — Economic |
| GRI | 203-1 | Inversiones en infraestructura y servicios apoyados | Topic Standard — Indirect Economic Impacts |
| GRI | 203-2 | Impactos económicos indirectos significativos | Topic Standard — Indirect Economic Impacts |
| GRI | 204-1 | Proporción de gasto en proveedores locales | Topic Standard — Procurement Practices |
| GRI | 205-1 | Operaciones evaluadas para riesgos de corrupción | Topic Standard — Anti-corruption |
| GRI | 205-2 | Comunicación y formación sobre anticorrupción | Topic Standard — Anti-corruption |
| GRI | 205-3 | Casos de corrupción confirmados | Topic Standard — Anti-corruption |
| GRI | 301-1 | Materiales utilizados por peso o volumen | Topic Standard — Materials |
| GRI | 301-2 | Insumos reciclados | Topic Standard — Materials |
| GRI | 302-1 | Consumo energético dentro de la organización | Topic Standard — Energy |
| GRI | 302-3 | Intensidad energética | Topic Standard — Energy |
| GRI | 302-4 | Reducción del consumo energético | Topic Standard — Energy |
| GRI | 303-2 | Gestión de impactos hídricos | Topic Standard — Water |
| GRI | 303-3 | Extracción de agua | Topic Standard — Water |
| GRI | 303-4 | Vertido de agua | Topic Standard — Water |
| GRI | 303-5 | Consumo de agua | Topic Standard — Water |
| GRI | 305-1 | Emisiones directas (Alcance 1) | Topic Standard — Emissions |
| GRI | 305-2 | Emisiones indirectas energía (Alcance 2) | Topic Standard — Emissions |
| GRI | 305-3 | Otras emisiones indirectas (Alcance 3) | Topic Standard — Emissions |
| GRI | 305-5 | Reducción de emisiones | Topic Standard — Emissions |
| GRI | 306-1 | Generación de residuos e impactos | Topic Standard — Waste |
| GRI | 306-2 | Gestión de impactos significativos | Topic Standard — Waste |
| GRI | 306-3 | Residuos generados | Topic Standard — Waste |
| GRI | 306-4 | Residuos no destinados a eliminación | Topic Standard — Waste |
| GRI | 306-5 | Residuos destinados a eliminación | Topic Standard — Waste |
| GRI | 307-1 | Incumplimiento de la legislación ambiental | Topic Standard — Environmental Compliance |
| GRI | 308-1 | Nuevos proveedores evaluados con criterios ambientales | Topic Standard — Supplier Environmental |
| GRI | 308-2 | Impactos ambientales negativos en cadena de suministro | Topic Standard — Supplier Environmental |
| GRI | 401-1 | Nuevas contrataciones y rotación de personal | Topic Standard — Employment |
| GRI | 401-2 | Beneficios para empleados a tiempo completo | Topic Standard — Employment |
| GRI | 401-3 | Permiso parental | Topic Standard — Employment |
| GRI | 403-1 | Sistema de gestión SST | Topic Standard — OHS |
| GRI | 403-2 | Identificación de peligros, evaluación de riesgos | Topic Standard — OHS |
| GRI | 403-3 | Servicios de salud en el trabajo | Topic Standard — OHS |
| GRI | 403-6 | Promoción de la salud de los trabajadores | Topic Standard — OHS |
| GRI | 403-9 | Lesiones por accidente laboral | Topic Standard — OHS |
| GRI | 403-10 | Dolencias y enfermedades laborales | Topic Standard — OHS |
| GRI | 404-1 | Horas medias de formación | Topic Standard — Training |
| GRI | 404-2 | Programas de formación y desarrollo | Topic Standard — Training |
| GRI | 404-3 | Evaluaciones periódicas de desempeño | Topic Standard — Training |
| GRI | 405-1 | Diversidad en órganos de gobierno y empleados | Topic Standard — Diversity |
| GRI | 405-2 | Ratio del salario base por género | Topic Standard — Diversity |
| GRI | 406-1 | Casos de discriminación | Topic Standard — Non-discrimination |
| GRI | 407-1 | Riesgos para la libertad de asociación | Topic Standard — Freedom of Association |
| GRI | 410-1 | Personal de seguridad capacitado en DDHH | Topic Standard — Security |
| GRI | 411-1 | Casos de violación de derechos de pueblos indígenas | Topic Standard — Indigenous Rights |
| GRI | 412-1 | Operaciones evaluadas para impactos en DDHH | Topic Standard — Human Rights |
| GRI | 412-2 | Formación de empleados en políticas de DDHH | Topic Standard — Human Rights |
| GRI | 412-3 | Acuerdos de inversión sometidos a evaluación DDHH | Topic Standard — Human Rights |
| GRI | 413-1 | Operaciones con participación de comunidad local | Topic Standard — Local Communities |
| GRI | 413-2 | Operaciones con impactos negativos en comunidades | Topic Standard — Local Communities |
| GRI | 414-1 | Nuevos proveedores evaluados con criterios sociales | Topic Standard — Supplier Social |
| GRI | 414-2 | Impactos sociales negativos en cadena de suministro | Topic Standard — Supplier Social |
| GRI | 416-1 | Evaluación de impactos en salud y seguridad de productos | Topic Standard — Customer H&S |
| GRI | 417-1 | Requisitos de información y etiquetado | Topic Standard — Marketing & Labeling |
| SASB | GHG Emissions | Tema general transversal | Aplica vía Industry Standards |
| SASB | Energy Mgmt | Tema general transversal | Aplica vía Industry Standards |
| SASB | Water Mgmt | Tema general transversal | Aplica vía Industry Standards |
| SASB | Waste Mgmt | Tema general transversal | Aplica vía Industry Standards |
| SASB | Materials Sourcing | Tema general transversal | Aplica vía Industry Standards |
| SASB | Environmental Mgmt | Marco general de gestión ambiental | Aplica vía Industry Standards |
| SASB | Labor Practices | Tema general transversal | Aplica vía Industry Standards |
| SASB | Health & Safety | Tema general transversal | Aplica vía Industry Standards |
| SASB | Human Rights | Tema general transversal | Aplica vía Industry Standards |
| SASB | Community Relations | Tema general transversal | Aplica vía Industry Standards |
| SASB | Supply Chain Mgmt | Tema general transversal | Aplica vía Industry Standards |
| SASB | Business Ethics | Tema general transversal | Aplica vía Industry Standards |
| ISSB-S1 | §27 | Estrategia: descripción del modelo de negocio | IFRS S1 |
| ISSB-S1 | §28 | Riesgos y oportunidades de sostenibilidad | IFRS S1 |
| ISSB-S1 | §29 | Establecimiento de metas | IFRS S1 |
| ISSB-S1 | §31 | Gobernanza: supervisión por máximo órgano | IFRS S1 |
| ISSB-S1 | §32 | Estrategia: recursos asignados | IFRS S1 |
| ISSB-S1 | §43-49 | Materialidad de información | IFRS S1 |
| ISSB-S1 | §62-87 | Métricas y objetivos | IFRS S1 |
| ISSB-S2 | §10-22 | Estrategia climática (riesgos físicos y de transición) | IFRS S2 |
| ISSB-S2 | §22 | Estrategia: planes de transición | IFRS S2 |
| ISSB-S2 | §29 | Métricas climáticas cross-industry | IFRS S2 |
| ISSB-S2 | §33-34 | Metas climáticas | IFRS S2 |
| BIC | Gobernanza | Dimensión Gobernanza — Decreto 2046/2019 | Reporte anual a Supersociedades |
| BIC | Trabajadores | Dimensión Trabajadores — Decreto 2046/2019 | Reporte anual a Supersociedades |
| BIC | Comunidad | Dimensión Comunidad — Decreto 2046/2019 | Reporte anual a Supersociedades |
| BIC | Medioambiente | Dimensión Medioambiente — Decreto 2046/2019 | Reporte anual a Supersociedades |
| BIC | Estrategia | Dimensión Misión y Estrategia — Decreto 2046/2019 | Reporte anual a Supersociedades |

---

## Tabla C — Regulación ESG colombiana

Úsala para marcar urgencia regulatoria. La columna "Preguntas conectadas" vincula
cada norma con los códigos internos del cuestionario de diagnóstico.

| Código norma | Nombre | Emisor | Aplica a | Obligación principal | Plazo / Periodicidad | Dimensión | Preguntas conectadas |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Ley 1901/2018 | Sociedades BIC | Congreso CO | Sociedades BIC | Marco habilitante de Sociedades BIC. Compromiso voluntario de impacto positivo en su objeto social. | Permanente | Multidimensional | GOB-C1-01, GOB-C1-04 |
| Decreto 2046/2019 | Reglamentación BIC | MinComercio | Sociedades BIC | Reporte anual de gestión a Supersociedades incluyendo las 5 dimensiones BIC (gobernanza, trabajadores, comunidad, medioambiente, estrategia). | 31 mayo anual | Multidimensional | GOB-C1-01, GOB-C1-04, GOB-C1-05, AMB-C1-01, VC-C1-08, VC-C1-10 |
| Ley 1715/2014 | Energías renovables | Congreso CO | Todas las empresas | Faculta acceso a incentivos tributarios por proyectos de energía renovable y eficiencia energética. | Permanente | Ambiental | AMB-C1-05, AMB-C2-05 |
| Ley 2169/2021 | Acción climática y carbono neutralidad | Congreso CO | Sector privado prioritario | Establece objetivo país de carbono neutralidad 2050 y resiliencia climática. | Plurianual | Ambiental | AMB-C1-03, AMB-C1-04, AMB-C2-01 a 04 |
| Ley 2232/2022 | Eliminación plásticos un solo uso | Congreso CO | Productores y comercializadores | Sustitución progresiva de plásticos de un solo uso. Fechas escalonadas hasta 2030. | Escalonado 2024-2030 | Ambiental | AMB-C1-07, AMB-C1-08 |
| Resolución 40103/2022 | Eficiencia energética industria | MinEnergía | Industria con consumo > umbral | Reporte de consumos energéticos al SICE. Diagnósticos energéticos obligatorios para grandes consumidores. | Anual | Ambiental | AMB-C1-05, AMB-C2-05 |
| CE 015/2025 (SFC) | Divulgación financiera ESG | SFC | Entidades vigiladas SFC | Reporte ISSB S1/S2 obligatorio progresivo. Plan de implementación abril 2026. | Escalonado desde 2026 | Multidimensional | GOB-C1-05, GOB-C1-08, AMB-C1-03, AMB-C1-04, AMB-C2-01 a 04, VC-C1-07, VC-C1-09 |
| CE 031/2021 (SFC) | Gestión riesgos climáticos | SFC | Entidades vigiladas SFC | Lineamientos para identificación, medición y gestión de riesgos climáticos. | Permanente | Gobernanza, Ambiental | GOB-C1-08, AMB-C1-04, AMB-C3-02 |
| Decreto 1072/2015 | SST — SG-SST | MinTrabajo | Todos los empleadores | Implementación obligatoria del Sistema de Gestión SST. Estándares mínimos por tamaño de empresa. | Permanente | Social-Trabajadores | TRB-C1-01, TRB-C2-03 |
| Ley 1010/2006 | Acoso laboral | Congreso CO | Todas las empresas | Prevención y sanción del acoso laboral. Comité de convivencia obligatorio. | Permanente | Social-Trabajadores | TRB-C1-05, TRB-C1-08 |
| Ley 361/1997 | Inclusión laboral discapacidad | Congreso CO | Empresas con vacantes | Garantías laborales para personas con discapacidad. Incentivos tributarios por contratación. | Permanente | Social-Trabajadores | TRB-C1-05, TRB-C2-06 |
| Decreto 280/2015 | Comisión ODS | Presidencia CO | Sector público y privado | Crea Comisión Interinstitucional ODS. Articula sector privado en agenda 2030. | Permanente | Estrategia | VC-C1-01, VC-C1-09 |
| CONPES 3918/2018 | Estrategia ODS | DNP | Sector público y privado | Estrategia nacional de implementación de ODS con seguimiento. | Plurianual | Estrategia | VC-C1-09 |

---

## Formato de salida y entregables

### Cómo mostrar resultados en pantalla (siempre)

Estás en una interfaz conversacional con una persona. **Nunca entregues JSON crudo
como respuesta principal** — es ilegible y la interfaz lo oculta. En su lugar:

- Presenta los resultados de cada etapa como una **tabla en español, legible**, con
  encabezados claros. Para M1: nombre, dimensión, descripción, fuente, relevancia
  sectorial, urgencia regulatoria Colombia, código.
- Acompaña la tabla con una lectura breve en prosa: qué destaca, qué implica para
  la empresa, qué sigue.
- Guarda el JSON estructurado internamente (lo necesitarás para etapas siguientes y
  para una eventual base de datos), pero no lo muestres salvo que te lo pidan.

### Cuándo generar archivos (entregables)

**No generes archivos automáticamente.** Muestra siempre la tabla en pantalla y
**ofrece** el entregable: "¿Quieres que lo exporte a Excel?". Genera el archivo solo
cuando la persona lo pida explícitamente. Esto respeta el control del usuario y
evita llenar el directorio de archivos no solicitados.

### Formato de entregable por etapa (cuando se pidan)

- **M1 (temas) y M5 (indicadores):** archivo **XLSX**. Son tablas que el cliente
  editará y compartirá.
- **M2 (encuesta a stakeholders):** archivo **CSV**. Es para distribuir o importar;
  formato simple.
- **M3 (matriz de materialidad):** **XLSX** con los datos de coordenadas y, si es
  posible, un gráfico de dispersión. (Un PDF visual de la matriz es deseable como
  mejora futura, no obligatorio en esta versión.)

### Regla de encoding (CRÍTICA para XLSX/CSV)

Al generar cualquier archivo, **conserva siempre las tildes y la ñ correctamente**.
Usa UTF-8 de extremo a extremo:

- Para XLSX con openpyxl: openpyxl maneja Unicode nativamente; escribe los strings
  en español tal cual (con tildes) sin convertir a Latin-1 ni escapar caracteres.
  Verifica que "dimensión", "código", "gestión" se vean correctos, no "dimensi?n".
- Para CSV: abre el archivo con `encoding='utf-8-sig'` (el BOM hace que Excel en
  Windows lo lea bien) o `encoding='utf-8'`, nunca con la codificación por defecto
  del sistema.
- Antes de entregar, revisa una celda con tilde para confirmar que no se rompió.

### Nombre de archivos

Usa nombres descriptivos y sin espacios: `temas_materiales_M1_[sector]_[fecha].xlsx`.

### Principio general

Sé concreto y accionable. Nada de materialidad de manual. La tabla y el archivo son
productos de consultoría de Horizonte Sostenible: deben verse profesionales.|
| --- | --- | --- | --- | --- | --- | --- | --- |
| Ley 1901/2018 | Sociedades BIC | Congreso CO | Sociedades BIC | Marco habilitante de Sociedades BIC. Compromiso voluntario de impacto positivo en su objeto social. | Permanente | Multidimensional | GOB-C1-01, GOB-C1-04 |
| Decreto 2046/2019 | Reglamentación BIC | MinComercio | Sociedades BIC | Reporte anual de gestión a Supersociedades incluyendo las 5 dimensiones BIC (gobernanza, trabajadores, comunidad, medioambiente, estrategia). | 31 mayo anual | Multidimensional | GOB-C1-01, GOB-C1-04, GOB-C1-05, AMB-C1-01, VC-C1-08, VC-C1-10 |
| Ley 1715/2014 | Energías renovables | Congreso CO | Todas las empresas | Faculta acceso a incentivos tributarios por proyectos de energía renovable y eficiencia energética. | Permanente | Ambiental | AMB-C1-05, AMB-C2-05 |
| Ley 2169/2021 | Acción climática y carbono neutralidad | Congreso CO | Sector privado prioritario | Establece objetivo país de carbono neutralidad 2050 y resiliencia climática. | Plurianual | Ambiental | AMB-C1-03, AMB-C1-04, AMB-C2-01 a 04 |
| Ley 2232/2022 | Eliminación plásticos un solo uso | Congreso CO | Productores y comercializadores | Sustitución progresiva de plásticos de un solo uso. Fechas escalonadas hasta 2030. | Escalonado 2024-2030 | Ambiental | AMB-C1-07, AMB-C1-08 |
| Resolución 40103/2022 | Eficiencia energética industria | MinEnergía | Industria con consumo > umbral | Reporte de consumos energéticos al SICE. Diagnósticos energéticos obligatorios para grandes consumidores. | Anual | Ambiental | AMB-C1-05, AMB-C2-05 |
| CE 015/2025 (SFC) | Divulgación financiera ESG | SFC | Entidades vigiladas SFC | Reporte ISSB S1/S2 obligatorio progresivo. Plan de implementación abril 2026. | Escalonado desde 2026 | Multidimensional | GOB-C1-05, GOB-C1-08, AMB-C1-03, AMB-C1-04, AMB-C2-01 a 04, VC-C1-07, VC-C1-09 |
| CE 031/2021 (SFC) | Gestión riesgos climáticos | SFC | Entidades vigiladas SFC | Lineamientos para identificación, medición y gestión de riesgos climáticos. | Permanente | Gobernanza, Ambiental | GOB-C1-08, AMB-C1-04, AMB-C3-02 |
| Decreto 1072/2015 | SST — SG-SST | MinTrabajo | Todos los empleadores | Implementación obligatoria del Sistema de Gestión SST. Estándares mínimos por tamaño de empresa. | Permanente | Social-Trabajadores | TRB-C1-01, TRB-C2-03 |
| Ley 1010/2006 | Acoso laboral | Congreso CO | Todas las empresas | Prevención y sanción del acoso laboral. Comité de convivencia obligatorio. | Permanente | Social-Trabajadores | TRB-C1-05, TRB-C1-08 |
| Ley 361/1997 | Inclusión laboral discapacidad | Congreso CO | Empresas con vacantes | Garantías laborales para personas con discapacidad. Incentivos tributarios por contratación. | Permanente | Social-Trabajadores | TRB-C1-05, TRB-C2-06 |
| Decreto 280/2015 | Comisión ODS | Presidencia CO | Sector público y privado | Crea Comisión Interinstitucional ODS. Articula sector privado en agenda 2030. | Permanente | Estrategia | VC-C1-01, VC-C1-09 |
| CONPES 3918/2018 | Estrategia ODS | DNP | Sector público y privado | Estrategia nacional de implementación de ODS con seguimiento. | Plurianual | Estrategia | VC-C1-09 |

---

## Formato de salida

- Datos para guardar/graficar (temas, coordenadas, indicadores) → **JSON válido**,
  sin markdown alrededor.
- Explicaciones para el cliente → prosa clara, adaptada a si es consultor o cliente
  final (ver CLAUDE.md).
- Sé concreto y accionable. Nada de materialidad de manual.
