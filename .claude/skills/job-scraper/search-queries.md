# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

LinkedIn y FreeHire para las consultas iniciales. Consultar las páginas de empleo de las empresas como respaldo.

## Query Categories

Selección provisional basada en la experiencia del CV. La prioridad inmediata es preparar una vacante concreta cuando Carlos comparta sus datos.

| Prioridad | Español | Inglés | Términos técnicos |
|-----------|---------|--------|-------------------|
| 1 | Desarrollador full-stack, Desarrollador backend | Full Stack Developer, Backend Developer | Python, FastAPI, Spring Boot, PostgreSQL |
| 2 | Desarrollador móvil, Desarrollador Flutter | Mobile Developer, Flutter Developer | Flutter, Dart, Firebase |
| 3 | Desarrollador IoT | IoT Developer | ESP32, Firebase, WebSockets |
| 4 | Ingeniero de software junior | Junior Software Engineer | REST APIs, TypeScript, Docker |

Para búsquedas web de respaldo, combinar cada título con `remoto México` o `remote Mexico` y uno de los términos técnicos.

## Location Filter

- Ideal: 100% remoto con contratación elegible desde México.
- Confirmar antes de clasificar: remoto sin países elegibles claros o con visitas presenciales ocasionales.
- Las vacantes híbridas o presenciales quedan fuera de la búsqueda general.
- Tiempo completo, sin restricción de horario declarada.
- Expectativa mínima: 25,000 MXN. Confirmar periodicidad y base bruta o neta antes de comparar.

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
