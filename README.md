# Diagnóstico Horizonte

Agente de Houston para **Horizonte Sostenible S.A.S. B.I.C.** — diagnóstico ESG,
análisis de materialidad y batería de indicadores GRI/SASB.

## Qué hace

Un agente orquestador que conduce dos flujos de trabajo:

- **Diagnóstico ESG** — cuestionario adaptativo de 102 preguntas en 5 dimensiones
  (Gobernanza, Ambiental, Social-Trabajadores, Social-Comunidad, Estrategia), con
  scoring por dimensión y nivel de madurez.
- **Análisis de materialidad (M1→M6)** — identificación de temas, consulta a
  stakeholders, matriz de materialidad, doble materialidad ESRS, mapeo a
  indicadores GRI/SASB y captura de datos.

Se adapta según hable con un consultor de Horizonte o con un cliente final.

## Estructura

```
diagnostico-horizonte/
├── houston.json          Manifiesto del agente (identidad, tabs)
├── CLAUDE.md             Instrucciones / rol del agente
├── README.md             Este archivo
└── skills/
    └── taller-materialidad/
        ├── SKILL.md       Procedimiento M1→M6
        └── referencias/
            ├── codigos_estandares.csv                 Disclosures GRI/SASB/ISSB/BIC
            ├── catalogo_estandares_tematicos_gri.csv  Catálogo maestro temático GRI
            └── regulacion_colombia.csv                Normativa ESG colombiana
```

## Cómo importar en Houston

1. Sube este repositorio completo a GitHub.
2. En Houston, abre **New Agent** y cambia a la pestaña **GitHub**.
3. Pega la URL del repositorio.
4. Houston descarga los archivos e instala el agente.

## Regla de oro

Los códigos de estándares (GRI/SASB/ISSB/ESRS) se leen siempre de los archivos de
referencia verificados en `skills/taller-materialidad/referencias/`. El agente
nunca inventa un código: si no está confirmado, lo señala como "por confirmar".
