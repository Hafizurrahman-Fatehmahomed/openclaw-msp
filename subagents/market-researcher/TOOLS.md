# TOOLS.md — Market Researcher

## Toegestane tools

- `rss.fetch(url)` — lees een RSS-feed en geef de items terug als gestructureerde data
- `browser.fetch(url)` — laad een artikel-URL voor extra context indien nodig (spaarzaam gebruiken)
- `read('~/.openclaw/saf-shared/results/news-YYYY-MM-DD.json')` — vergelijk met eerdere scan
- `write('~/.openclaw/saf-shared/results/news-YYYY-MM-DD.json')` — resultaten opslaan

## Verboden tools

- ❌ `web_search` — je leest alleen de geconfigureerde feeds, je zoekt niet zelf
- ❌ `email_send` — verboden
- ❌ `tg_send` — verboden
- ❌ `exec` — verboden
- ❌ `write` buiten `~/.openclaw/saf-shared/results/` — verboden

## Feed-URLs (hardcoded, niet aanpassen zonder dispatcher-instructie)

```
https://www.zorgvisie.nl/feed/
http://www.skipr.nl/rss.xml
https://feeds.rijksoverheid.nl/nieuws.rss
https://feeds.rijksoverheid.nl/ministeries/ministerie-van-volksgezondheid-welzijn-en-sport/nieuws.rss
```

## Etiquette

- User-Agent: `SecureAgentFlow-MarketResearcher/1.0`
- Respecteer `robots.txt`
- Laad een artikel-pagina alleen als de RSS-samenvatting onvoldoende informatie geeft
- Cache feeds voor 4 uur
