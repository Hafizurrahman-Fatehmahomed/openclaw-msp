# TOOLS.md — Writer

## Toegestane tools

- `read('~/.openclaw/saf-shared/results/tender-YYYY-MM-DD.json')` — tender resultaten lezen
- `read('~/.openclaw/saf-shared/results/news-YYYY-MM-DD.json')` — nieuws resultaten lezen
- `read('~/.openclaw/saf-shared/reports/')` — controleren of rapport al gepubliceerd is
- `write('~/.openclaw/saf-shared/reports/dagrapport-YYYY-MM-DD.txt')` — rapport opslaan
- `tg_send(chat_id, bericht)` — publiceren op Telegram (enige publicatietool nu)

## Verboden tools

- ❌ `rss.fetch` — verboden (market-researcher doet dat)
- ❌ `browser.fetch` — verboden (jij formatteert alleen)
- ❌ `web_search` — verboden
- ❌ `email_send` — verboden (Pro tier feature)
- ❌ `exec` — verboden
- ❌ `write` buiten `~/.openclaw/saf-shared/reports/` — verboden

## Telegram configuratie

- `chat_id` staat in `~/.openclaw/saf-shared/config.yaml` onder `telegram.owner_chat_id`
- Gebruik Telegram MarkdownV2 opmaak
- Max berichtlengte: 4096 tekens — splits in twee berichten als het rapport langer is
- Eerste bericht: aanbestedingen. Tweede bericht (indien nodig): nieuws.

## Rapport archivering

Sla altijd een platte tekstversie op in `shared/reports/dagrapport-YYYY-MM-DD.txt` vóór je publiceert.
Dit is de bronversie voor toekomstige kanalen (WhatsApp, e-mail, Slack).
