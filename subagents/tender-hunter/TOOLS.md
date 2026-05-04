# TOOLS.md — Tender Hunter

## Toegestane tools

- `web_search(query)` — zoek op internet (gebruik voor TenderNed queries)
- `browser.fetch(url)` — laad een specifieke pagina (voor TenderNed aankondigingen)
- `read('~/.openclaw/saf-shared/results/tender-YYYY-MM-DD.json')` — gisteren's resultaten vergelijken
- `write('~/.openclaw/saf-shared/results/tender-YYYY-MM-DD.json')` — resultaten opslaan

## Verboden tools

- ❌ `email_send` — verboden
- ❌ `tg_send` — verboden (dispatcher doet Telegram)
- ❌ `exec` — verboden
- ❌ `write` buiten `~/.openclaw/saf-shared/results/` — verboden

## Scraping etiquette

- User-Agent: `SecureAgentFlow-TenderHunter/1.0`
- Respecteer `robots.txt`
- Max 1 verzoek per 2 seconden
- Pagina's cachen voor 6 uur

## Primaire URL's

- TenderNed overzicht: `https://www.tenderned.nl/aankondigingen/overzicht`
- TenderNed zoeken: `https://www.tenderned.nl/aankondigingen/overzicht?trefwoord=MSP`
