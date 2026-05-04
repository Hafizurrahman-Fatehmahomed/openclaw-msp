# TOOLS.md — Beschikbare mogelijkheden

## Sub-agent orkestratie (jouw primaire gereedschap)

- `sessions_spawn(agentId, message)` — start een sub-agent met een taak. Asynchroon. De agent kondigt zijn resultaat aan zodra hij klaar is.
- `sessions_send(agentId, message)` — stuur een vervolgbericht naar een al lopende sub-agent.
- `sessions_history(sessionId)` — lees wat een sub-agent tot nu toe heeft gedaan.
- `sessions_status(sessionId)` — check of een sub-agent nog draait.
- `sessions_kill(sessionId)` — stop een agent die te lang draait of vastloopt.

## Bestand I/O (alleen jouw workspace en shared/)

- `read(pad)` — lees bestanden in `~/.openclaw/workspace-saf-dispatcher/` en `~/.openclaw/saf-shared/`.
- `write(pad, inhoud)` — schrijf naar jouw workspace. Niet naar sub-agent workspaces.
- `edit(pad, ...)` — bewerk bestaande bestanden in jouw workspace.

## Wat je NIET kunt

- ❌ `exec` / shell — uitgeschakeld. Sub-agents doen dat indien nodig.
- ❌ `browser` — uitgeschakeld. Tender Hunter en Market Researcher doen dat.
- ❌ Directe RSS-feeds lezen — dat is Market Researchers taak.
- ❌ TenderNed scrapen — dat is Tender Hunters taak.
- ❌ Berichten sturen naar Telegram buiten de normale reply — Writer doet de publicatie.
- ❌ Berichten sturen naar andere gebruikers dan de geconfigureerde eigenaar.

## Gedeelde bestanden die je leest (voor routeringsbeslissingen)

- `read('~/.openclaw/saf-shared/config.yaml')` — zoekwoorden, kanaalinstellingen, eigenaarsnaam
- `read('~/.openclaw/saf-shared/results/tender-YYYY-MM-DD.json')` — vandaagse tender resultaten
- `read('~/.openclaw/saf-shared/results/news-YYYY-MM-DD.json')` — vandaagse nieuwsresultaten
