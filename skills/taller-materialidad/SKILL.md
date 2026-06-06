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
- **codigo_estandar**: el código específico SOLO si lo verificas en
  `referencias/codigos_estandares.csv`. Si no está ahí, deja el campo como
  "por confirmar" y dilo. **Nunca inventes un código.** (Ver regla abajo.)

Devuelve esto como **JSON válido**, array de objetos, sin markdown ni texto
adicional alrededor, para que se pueda guardar directamente.

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

Etiqueta cada punto por dimensión E/S/G. Entrega las coordenadas como JSON para
graficar, y una lectura en prosa de qué significan los resultados para la empresa.

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
los 200 de GRI — solo los que aplican al tema y al sector). Apóyate primero en
`referencias/catalogo_estandares_tematicos_gri.csv` para ubicar el estándar
temático correcto (ej. tema "gestión de residuos" → GRI 306 Residuos), y luego en
`referencias/codigos_estandares.csv` para el código fino del disclosure. Para cada
indicador:

- nombre del indicador
- **código** (leído de `referencias/codigos_estandares.csv`)
- descripción
- unidad de medida
- frecuencia de reporte sugerida
- fuente de datos recomendada (de dónde sale el dato dentro de la empresa)

Cruza también con `referencias/regulacion_colombia.csv`: si un tema está cubierto
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

Los códigos GRI/SASB/ISSB/ESRS solo se toman de los archivos de referencia
verificados de esta skill. Estos archivos se siembran en el directorio de trabajo
del agente bajo la ruta `skills/taller-materialidad/referencias/`. Si no los
encuentras en esa ruta exacta, búscalos por nombre en todo el directorio de
trabajo antes de concluir que faltan (los nombres son únicos):

- `codigos_estandares.csv` — disclosures finos (a nivel de contenido,
  ej. GRI 305-1, GRI 306-2) de GRI, SASB, ISSB-S1, ISSB-S2 y BIC con su tema,
  validados por Horizonte Sostenible. Úsalo para el código exacto de un indicador.
- `catalogo_estandares_tematicos_gri.csv` — catálogo MAESTRO de todos
  los Estándares Temáticos GRI (series 200 económica, 300 ambiental, 400 social),
  con código, nombre oficial y dimensión E/S/G. Úsalo en M1 y M5 para barrer el
  universo completo de temas posibles y no dejar ningún estándar GRI por fuera.
- `regulacion_colombia.csv` — 13 normas colombianas con emisor,
  obligación, plazo, dimensión y preguntas del cuestionario conectadas.

**Cobertura de temas en M1:** recorre el catálogo maestro temático para asegurar
que consideraste todas las áreas GRI relevantes al sector antes de cerrar la lista
de candidatos. Recuerda que los temas materiales dependen del sector: usa criterio
para descartar los que no apliquen y justifica por qué (como exige GRI 3).

Si un código no está en estos archivos, **no lo inventes**. Di "el código exacto
debe confirmarse contra la versión vigente del marco". Un código falso en un
entregable destruye la credibilidad técnica de Horizonte. Más vale un "por
confirmar" honesto.

## Formato de salida

- Datos para guardar/graficar (temas, coordenadas, indicadores) → **JSON válido**,
  sin markdown alrededor.
- Explicaciones para el cliente → prosa clara, adaptada a si es consultor o cliente
  final (ver CLAUDE.md).
- Sé concreto y accionable. Nada de materialidad de manual.
