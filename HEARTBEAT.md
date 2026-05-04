# HEARTBEAT.md — Geplande taken

OpenClaw pollt dit bestand elke 30 minuten. Wanneer een taak op de planning staat, voer je die uit door de juiste sub-agent te spawnen.

## Dagelijks schema (werkdagen maandag t/m vrijdag)

```
06:00 — spawn tender-hunter
        Taak: "Eerste dagelijkse scan. Zoek op TenderNed naar: MSP, ICT Zorg, MSP Zorg.
               Sla resultaten op in shared/results/tender-YYYY-MM-DD.json.
               Vergelijk met gisteren — markeer nieuwe aanbestedingen."

06:00 — spawn market-researcher
        Taak: "Eerste dagelijkse scan. Lees RSS-feeds: Zorgvisie, Skipr, Rijksoverheid, VWS.
               Filter relevante zorg-artikelen. Sla op in shared/results/news-YYYY-MM-DD.json."

06:45 — spawn writer
        Taak: "Maak dagrapport op basis van tender en nieuws resultaten van vandaag.
               Publiceer om 07:00 op Telegram. Formaat: zie AGENTS.md van writer."

14:00 — spawn tender-hunter
        Taak: "Tweede dagelijkse scan. Zoek nieuwe aanbestedingen gepubliceerd na 06:00 vandaag.
               Voeg eventuele nieuwe toe aan shared/results/tender-YYYY-MM-DD.json.
               NIET opnieuw publiceren — opslaan voor morgenochtend."

14:00 — spawn market-researcher
        Taak: "Tweede dagelijkse scan. Lees RSS-feeds op nieuwe artikelen na 06:00.
               Voeg relevante toe aan shared/results/news-YYYY-MM-DD.json.
               NIET opnieuw publiceren — opslaan voor morgenochtend."
```

## Weekelijks schema

```
Maandag 06:00 — voeg aan tender-hunter taak toe:
        "Controleer ook aanbestedingen uit het weekend (zaterdag + zondag).
         Markeer eventuele nieuwe die gemist zijn."
```

## Maandelijks

```
Eerste werkdag van de maand, 06:00 — voeg aan writer taak toe:
        "Voeg een maandoverzicht toe aan het dagrapport:
         totaal aantal tenders gevonden, totaal nieuwsartikelen, opvallende trends."
```

## Weekend

- Zaterdag en zondag: GEEN geplande scans, GEEN dagrapport.
- Uitzondering: als eigenaar handmatig vraagt, altijd uitvoeren.

## Vakantie/afwezigheid

Als eigenaar meldt "ik ben weg tot [datum]":
- Schrijf `afwezig_tot: YYYY-MM-DD` in MEMORY.md
- Onderdruk de 07:00 publicatie (Tender Hunter en Market Researcher blijven WEL scannen en opslaan)
- Op terugkeerdag: spawn writer voor een inhaalrapport van alle gemiste dagen

## Bij heartbeat poll

1. Check het huidige tijdstip.
2. Is er een taak die nu uitgevoerd moet worden? → uitvoeren.
3. Niets gepland? → schrijf alleen `heartbeat ok` naar MEMORY.md log. Stuur NIETS naar de eigenaar.
