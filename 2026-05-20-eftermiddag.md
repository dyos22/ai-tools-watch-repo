# AI-verktygsspaning — 2026-05-20 (eftermiddag)

**Extrakörning** samma dag som morgonrapporten, för att fånga det som hänt sen 09:22. Tre parallella svep över Hacker News + GitHub + ProductHunt, Reddit (LocalLLaMA + MachineLearning + ChatGPTCoding + singularity), och nyhetsbreven + HuggingFace + Lobste.rs. 9 fynd. Allt som redan stod i 19 maj eller morgonens 20 maj-rapport har medvetet plockats bort — totalt cirka 14 dubbletter ratades (ViMax, DramaBox, Nova3D, OmniVoice, Khala, Pixal3D, Supertonic 3, Forge, Semble, CodeGraph, Superlog, SmallCode, id-agent, Manus Cloud Computer).

## Topp 3 att testa direkt

1. **Z Image Turbo** — den nya text-till-bild-favoriten just nu, gör en hyfsad bild på under en sekund direkt i webbläsaren. Snabbare än de flesta etablerade alternativen.
2. **yapsnap** — skriv av valfri YouTube/TikTok/Instagram-video till text på din egen dator, utan grafikkort och utan att skicka ljudet till någons moln.
3. **anything-to-notebooklm** — släng in en låst tidningsartikel, en YouTube-video, ett PDF eller en podcast, och få ut en podd, ett mindmap, en infografik eller en quiz — automatiskt.

---

## Skapa saker med AI

### Z Image Turbo — sekundsnabb text-till-bild
**Vad det är:** En text-till-bild-modell som spottar ut färdiga bilder på under en sekund, hostad gratis på HuggingFace. Bygger på Tencents nya Z Image-arkitektur.

**Varför det är intressant:** Snabbhet är ett eget värde — när varje bild tar 30 sekunder att generera (som t.ex. Midjourney och Flux) blir kreativt experimenterande tungrott. Z Image Turbo gör 20+ varianter på samma tid och har på två veckor seglat upp som en av de mest gillade modellerna på HuggingFace.

**Buzz-nivå:** Håller på att bli en grej — 3 190 likes på HuggingFace-spacet, 74 öppna diskussionstrådar. Snabb spridning bland AI-konstnärer på Twitter.

**Testa:** [huggingface.co/spaces/mrfakename/Z-Image-Turbo](https://huggingface.co/spaces/mrfakename/Z-Image-Turbo) — klicka in och skriv en prompt, ingen installation behövs.

### Scenema Audio — röst-AI byggd på en video-AI
**Vad det är:** En röst-klonare som kan kopiera vilken röst som helst från ett kort ljudprov och dessutom styras med skjutreglage för känsla, andetag och tempo. Det udda är att den är byggd ovanpå Lightricks videogeneratorn LTX 2.3 — alltså samma "hjärna" som gör filmklipp har återanvänts för ljud.

**Varför det är intressant:** ElevenLabs och DramaBox (förra rapporten) är specialbyggda för röst. Scenema visar att den nyare typen av "video-AI" (diffusion transformers) kan göra både rörlig bild och tal — vilket öppnar för helt nya verktyg där läpprörelser, video och röst skapas i ett svep, av samma modell. Mycket tidigt men intellektuellt spännande.

**Buzz-nivå:** Extremt tidigt — 27 likes på HuggingFace, postat av Apolinário (samma curator som lyfte Khala för två dagar sen).

**Testa:** [huggingface.co/spaces/multimodalart/scenema-audio](https://huggingface.co/spaces/multimodalart/scenema-audio) — körs i webbläsaren, gratis.

### yapsnap — transkribera vad som helst utan grafikkort
**Vad det är:** Ett litet kommandoradsverktyg som tar en länk till en YouTube-, TikTok-, X- eller Instagram-video och spottar ut en textfil med vad som sägs. Allt händer på din egen dator, ingen molnlöptid, inget grafikkort behövs.

**Varför det är intressant:** OpenAIs Whisper är guldstandarden men kräver grafikkort för att gå snabbt. Molntjänster som Otter och Rev kostar pengar och skickar ljudet utomlands. yapsnap använder en pytteliten modell (~80 MB) som klarar 10+ språk på CPU. Du laddar ner den en gång och kan sen transkribera obegränsat utan internet. Perfekt om du t.ex. vill ha utskrift av podcast-avsnitt, föreläsningar eller intervjuer.

**Buzz-nivå:** Extremt tidigt — 98 stjärnor på GitHub, postad på Hacker News för 9 timmar sen med 55 punkter. Pre-buzz-läge.

**Testa:** [github.com/kouhxp/yapsnap](https://github.com/kouhxp/yapsnap) — kräver att man kan installera ett Python-paket. En utvecklarkollega kan slänga upp det åt dig på 5 minuter, sen är det "yapsnap <länk>" som gäller.

### SetPose — 3D-docka för konstnärer, direkt i webbläsaren
**Vad det är:** En interaktiv 3D-docka du kan posera precis hur du vill — böja, vrida, rotera leder, ändra kameravinkel och belysning. Plus färdiga poser, djur, anime-modeller och rekvisita att lägga in. Tänk som de gamla träfigurerna från konstaffären, men i webbläsaren, gratis och oändligt anpassningsbar.

**Varför det är intressant:** Inte AI-genererad i vanlig mening — det är ett klassiskt 3D-posverktyg — men gick upp på Hacker News som ett verktyg AI-konstnärer använder för att generera referensbilder och pose-data att mata in i Midjourney eller Flux ("ge mig den här posen, fast i ett rymdlandskap"). Bättre än att försöka beskriva poser i ord.

**Buzz-nivå:** Börjar fångas upp — 87 punkter och 32 kommentarer på Hacker News, postat för en dag sedan.

**Testa:** [setpose.com](https://setpose.com/) — gratis i webbläsaren, ingen registrering. Pro-version finns för flera figurer i samma scen.

---

## Gör Claude Code och andra AI-assistenter smartare

Du använder ju Claude Code — här är tre verktyg från idag/i går som är värt att känna till.

### Codebuff — Claude Code-rival med 61 % rätt mot Claudes 53 %
**Vad det är:** Ett alternativ till Claude Code som körs från terminalen och kan plugga in vilken AI-modell som helst — Claude, GPT, Qwen, DeepSeek. Använder en "lagsetup" där olika små AI:n får specialroller (en letar filer, en planerar, en redigerar, en granskar).

**Varför det är intressant:** Skaparna påstår att Codebuff slår Claude Code (61 % vs 53 % rätt) på 175 testuppgifter — tagna med en nypa salt eftersom det är deras egna tester, men noterbart är att de släpper rådata. För dig som privatperson är finessen att du kan välja billigare/öppna modeller och därmed sänka kostnaden om Claude Codes prenumeration känns tung.

**Buzz-nivå:** Snabbväxande — 5 600 stjärnor och +500 denna vecka.

**Länk:** [github.com/CodebuffAI/codebuff](https://github.com/CodebuffAI/codebuff)

### Orca (Stably) — kontrollpanel för flera AI-arbetare samtidigt
**Vad det är:** En desktop- och mobilapp där du kan ha flera AI-assistenter (Claude Code, Codex, Grok, Gemini m.fl.) arbetande parallellt på olika delar av ett projekt — och själv övervaka dem från en gemensam vy istället för att tabba runt.

**Varför det är intressant:** Om ett enskilt AI-bygge tar 20 minuter och två parallella tar 25 minuter — varför inte köra tre eller fyra samtidigt? Orca är det första riktiga försöket att göra det här lättanvänt. Mobilappen är extra smart: starta en agent från datorn, kolla resultatet från soffan.

**Buzz-nivå:** Het — 3 000 stjärnor, +656 denna vecka. Version 1.4.15 släpptes idag (21 maj enligt repots ändringsdatum).

**Länk:** [github.com/stablyai/orca](https://github.com/stablyai/orca)

### Warp Oz — "kontrolltornet" för molnbaserade AI-arbetare
**Vad det är:** Terminal-verktyget Warp släppte i veckan en överbyggnad som heter Oz: en enda vy där du kan se och styra alla AI-agenter du har igång i molnet — oavsett om de bygger på Claude Code, Codex eller Warps egna agent.

**Varför det är intressant:** Lite samma idé som Orca ovan, men Oz fokuserar på agenter som kör på molnservrar dygnet runt (som Manus Cloud Computer i förra rapporten). Tänk: 3 agenter som spanar på olika sajter åt dig, plus 2 som programmerar — en enda app att kolla istället för fem flikar. Också integrerad budget- och kostnadstak per agent.

**Buzz-nivå:** Lanserades med stor uppmärksamhet i TLDR AI:s morgonbrev 20 maj.

**Länk:** [warp.dev/blog/multi-harness-cloud-agent-orchestration](https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration)

---

## Specialgrejer & experiment

### anything-to-notebooklm — automatfabrik för podd, mindmap, infografik
**Vad det är:** Ett verktyg som tar nästan vilken källa som helst (paywallad tidningsartikel, YouTube-video, podcast-avsnitt, PDF, Excel, Word, Twitter-tråd, podcast, WeChat-artikel — 15+ källtyper) och förvandlar den automatiskt till ett av åtta utdataformat: podcast, PowerPoint, mindmap, quiz, video, rapport, infografik eller flashcards.

**Varför det är intressant:** Googles eget NotebookLM kräver att du själv klipper-och-klistrar in materialet. Det här verktyget hämtar källan åt dig — och har dessutom en avancerad mekanism för att komma runt betalmurar (NYT, WSJ, The Economist nämns explicit). Säg bara "gör en podd av den här WSJ-artikeln" och få färdig ljudfil tillbaka. Etiskt gränsfall — använd ansvarsfullt.

**Buzz-nivå:** Håller på att bli en grej — 4 300 stjärnor på GitHub, +2 526 (!) denna vecka. Närmar sig tröskeln för "för stor för spaning" men just nu mitt i sweet spot.

**Länk:** [github.com/joeseesun/qiaomu-anything-to-notebooklm](https://github.com/joeseesun/qiaomu-anything-to-notebooklm)

### Carbon — AI som "skriver" DNA
**Vad det är:** En AI-modell som hanterar DNA-sekvenser ungefär som ChatGPT hanterar text. Du matar in en del av en gen och den föreslår vad som kan komma härnäst, eller bedömer om en specifik mutation är farlig eller harmlös. Tre storlekar (0.5B, 3B, 8B parametrar) finns gratis på HuggingFace.

**Varför det är intressant:** Det här är "ChatGPT för biologer" — men byggt på riktig DNA-data istället för internet-text. Carbon-3B har på kort tid fått 2 180 likes, vilket är en stor signal i en nischad domän. Inte direkt något du själv kommer använda, men illustrerar hur snabbt AI-teknik nu spiller över i biotech och läkemedelsforskning. För nyfikenhet: prova demon i webbläsaren — den visar grafiskt vad modellen "tror" om DNA-sekvensen du klistrar in.

**Buzz-nivå:** Färskt — 60 likes på själva demon, men 2 180 likes på modellkortet.

**Testa:** [huggingface.co/spaces/HuggingFaceBio/carbon-demo](https://huggingface.co/spaces/HuggingFaceBio/carbon-demo)

### PapersWithCode lever igen — AI-forskningens karta är tillbaka
**Vad det är:** PapersWithCode var i flera år den självklara platsen för att hitta "den bästa AI-modellen för X just nu" — med toplistor per uppgift, kod till varje paper, och rankningar. Meta köpte den och lät den dö. Nu har en HuggingFace-anställd byggt upp en kopia på en ny adress och håller den uppdaterad med AI-assistans.

**Varför det är intressant:** Inte ett "verktyg" du själv kör, men en plats du kan referera till om du undrar "vilken är bästa öppna text-till-tal-modellen just nu?" eller "vilken röstigenkänning är ledande?". Hjälper dig att inte fastna i förra årets favoriter.

**Buzz-nivå:** Färskt — postat för 3 dagar sen, 342 upvotes och 30 kommentarer i r/MachineLearning. Verifierad av HuggingFace-teamet, så projekt är inte ensligt.

**Länk:** [paperswithcode.co](https://paperswithcode.co/)

---

## Metodnoter

**Källor jag nådde:** Hacker News (front + show + newest), GitHub Trending (allt + Python + TypeScript), HuggingFace (spaces + models + papers), Lobste.rs, Reddit (LocalLLaMA + MachineLearning + ChatGPTCoding + singularity, via stealth-extraktion eftersom WebFetch fortsatt blockeras), nyhetsbreven TLDR AI 19+20 maj och The Rundown, plus Ben's Bites-arkivet.

**Källor som krånglade:** Product Hunt AI-kategorin returnerade 404. Ben's Bites visade bara rubriker men ingen brödtext (Substack-paywall för full text). Reddit-veckotopplistan dominerades av Qwen-spekulationer och meta-diskussioner om hallucinationer i forskningspapper — mindre konkret verktygsmaterial än normalt.

**Dubbletter som ratades** (jämfört med 19 maj och morgonens 20 maj-rapport): ViMax, DramaBox, Nova3D, OmniVoice, Khala, Pixal3D, Supertonic 3, MiniCPM-V 4.6, Forge, Semble, CodeGraph, Beacon, id-agent, SmallCode, Superlog, Manus Cloud Computer, Equibles, HRM-Text-1B, Odyssey Agora-1, Wireloom. Totalt ~14 fynd som annars hade kvalat in valdes bort för att inte upprepa redan rapporterade verktyg.

**Vad jag exkluderade utöver dubbletter:**
- NVIDIA LongLive 1.0 (real-tids lång videogenerering) — släpps av NVIDIA, faller in under "stora releases från storbolag".
- ByteDance Lance (3B multimodal) — storbolag, exkluderas.
- Gemini 3.5 Flash, Cursor Composer 2.5, OpenAI Codex Mobile — alla "stora releases" från etablerade aktörer.
- Antigravity 2.0 (Google), Karpathy-till-Anthropic — viktig nyhet, inte ett verktyg du själv kan testa.
- IgniteMS (batch-embeddings) — för djupt teknisk för icke-utvecklare, 0 stjärnor på GitHub vilket också är osäkert.
- Expediter — bara 0 stjärnor och nischat (macOS-only, för Claude Code-jonglerare), Orca täcker samma idé bättre.
- xAI Grok Skills och Lovable Skills — funktionsuppdateringar inom befintliga prenumerationer, inte fristående verktyg.
