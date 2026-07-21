# Instruktioner för AI-verktygsspaning

Dessa preferenser gäller för alla framtida körningar av spaningsroutinen.

## Filtreringsregler

### Exkludera ALLTID:
- Verktyg som **redan tagits upp i en tidigare rapport** (se uteslutningslistan byggd från tidigare datum-filer) — om inte en *stor* ny utveckling skett sedan dess (ny version med tydligt ny förmåga, eller stort hopp i genomslag). I så fall: markera "Uppföljning" och beskriv i en mening vad som är nytt.

### Exkludera INTE:
- Verktyg pga. att de kommer från stora aktörer (OpenAI, Google, Anthropic, Microsoft, Meta m.fl.) — om något är genuint nytt och intressant är det lika relevant oavsett vem som gjort det.
- Verktyg pga. GitHub-stjärnorräknat. Stjärnor är enbart en **buzz-signal** att rapportera (t.ex. "håller på att bli en grej — 25 000 stjärnor"), inte ett uteslutningskriterium.

### Lägre prioritet (ta bara med om exceptionellt):
- Bild-, film- och röst/ljud-verktyg (inklusive musik och text-till-tal) — ta bara med om helt ny förmåga, inte "ännu en öppen TTS- eller bildmodell"

### Stora aktörer & hög buzz — EGEN SEKTION, inte exkluderade:
Verktyg och releaser från OpenAI, Google, Anthropic, Microsoft, Meta m.fl., samt verktyg med väldigt hög buzz (10 000+ GitHub-stjärnor) ska INTE filtreras bort — de ska placeras i en **separat sektion** i rapporten: **"Stora aktörers nyheter & mainstream-buzz"**. Inkludera bara om det är genuint nytt eller en förmåga som inte funnits förut — inte generella uppdateringar.

## Inriktning

Prioritera: **agenter, verktyg, infrastruktur, automation, praktiska tillämpningar**

Användarprofil: icke-teknisk svensk användare som är intresserad av att följa AI-utvecklingen och som använder Claude Code.

## Rapportstruktur (standardmall)

1. Inledning — kort intro
2. **Topp 3 att testa direkt** — de tre mest användbara fynden, en mening var. Prioritera agenter/verktyg/infrastruktur.
3. **Gör Claude Code och andra AI-assistenter smartare** — verktyg som förbättrar AI-kodningsassistenter, förklarat i klarspråk
4. **Verktyg, automation & infrastruktur** — rapportens tyngdpunkt
5. **Specialgrejer & experiment** — nischade fynd och forskningsexperiment
6. **Stora aktörers nyheter & mainstream-buzz** — releaser och verktyg från OpenAI, Google, Anthropic, Microsoft, Meta m.fl., samt verktyg med extremt hög buzz (10 000+ stjärnor). Inkludera bara om det är genuint nytt. Hoppa över sektionen om inget relevant finns denna vecka.
7. **Skapa saker med AI** — 0–2 fynd, bara om exceptionella. Hoppa över sektionen om inget exceptionellt finns.
8. **Metodnoter** — vilka källor som nåddes, vad som exkluderades, antal dubbletter mot tidigare rapporter

## Stil

- Skriv på populärvetenskaplig svenska
- Undvik otekniska termer som "embeddings", "transformer", "tokens" utan förklaring
- Konkreta exempel slår abstrakta beskrivningar
- Jämför med saker läsaren känner till: ChatGPT, Cursor, Claude Code
