# Instruktioner för AI-verktygsspaning

Dessa preferenser gäller för alla framtida körningar av spaningsroutinen.

## Filtreringsregler

### Exkludera ALLTID:
- Verktyg som **redan tagits upp i en tidigare rapport** (se uteslutningslistan byggd från tidigare datum-filer) — om inte en *stor* ny utveckling skett sedan dess (ny version med tydligt ny förmåga, eller stort hopp i genomslag). I så fall: markera "Uppföljning" och beskriv i en mening vad som är nytt.
- **Stora mainstreams releases** från OpenAI, Google, Anthropic, Microsoft, Meta — de når allmänt kände användare på egen hand utan att vi behöver lyfta dem.
- **Generella foundation models** (nya versioner av GPT, Gemini, Claude, Llama etc.)

### Exkludera INTE enbart pga. GitHub-stjärnor:
- Stjärnorräknaren är ett trubbigt mått. Många stjärnor kan betyda mycket buzz, men det är inte ett tillräckligt skäl att utesluta något.
- Stjärnor ska i stället **rapporteras som buzz-signal** (t.ex. "håller på att bli en grej — 25 000 stjärnor") och läsaren får bedöma.
- Uteslut ett verktyg pga. genomslag bara om det är **allmänt känt och omskrivet i mainstream-press** (TechCrunch, Wired, The Verge, svenska nyhetstidningar) — inte baserat på stjärnräknet.

### Lägre prioritet (ta bara med om exceptionellt):
- Bild-, film- och röst/ljud-verktyg (inklusive musik och text-till-tal) — ta bara med om helt ny förmåga, inte "ännu en öppen TTS- eller bildmodell"

## Inriktning

Prioritera: **agenter, verktyg, infrastruktur, automation, praktiska tillämpningar**

Användarprofil: icke-teknisk svensk användare som är intresserad av att följa AI-utvecklingen och som använder Claude Code.

## Rapportstruktur (standardmall)

1. Inledning — kort intro
2. **Topp 3 att testa direkt** — de tre mest användbara fynden, en mening var. Prioritera agenter/verktyg/infrastruktur.
3. **Gör Claude Code och andra AI-assistenter smartare** — verktyg som förbättrar AI-kodningsassistenter, förklarat i klarspråk
4. **Verktyg, automation & infrastruktur** — rapportens tyngdpunkt
5. **Specialgrejer & experiment** — nischade fynd och forskningsexperiment
6. **Skapa saker med AI** — 0–2 fynd, bara om exceptionella. Hoppa över sektionen om inget exceptionellt finns.
7. **Metodnoter** — vilka källor som nåddes, vad som exkluderades, antal dubbletter mot tidigare rapporter

## Stil

- Skriv på populärvetenskaplig svenska
- Undvik otekniska termer som "embeddings", "transformer", "tokens" utan förklaring
- Konkreta exempel slår abstrakta beskrivningar
- Jämför med saker läsaren känner till: ChatGPT, Cursor, Claude Code
