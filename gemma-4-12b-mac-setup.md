# Köra Gemma 4 12B lokalt på Mac (Apple Silicon)

> Praktisk installationsguide — uppdaterad 4 juni 2026

## Vad det är

**Gemma 4 12B** är Googles nya öppna modell, släppt 3 juni 2026 under Apache 2.0-licens. Den är *encoder-free multimodal* — samma modell hanterar text, bild, ljud och video utan separata kodarnätverk — och är byggd för att köras **lokalt** på en vanlig laptop. Allt stannar på din dator: inget skickas till molnet, inga API-kostnader.

Det som gör den intressant för Mac specifikt: Ollama körs numera på **MLX** på Apple Silicon, vilket utnyttjar det enhetliga minnet (unified memory) effektivt. En M2 Pro med 16 GB klarar 12B-modellen i kvantiserad form.

---

## Hårdvarukrav

| | Minimum | Rekommenderat |
|---|---|---|
| **Mac** | Apple Silicon (M1 eller senare) | M2 Pro / M3 / M4 |
| **Unified memory** | 16 GB (Q4-kvantiserad) | 24–32 GB (mer kontext + andra appar) |
| **Disk** | ~9–10 GB ledigt (Q4) | 20+ GB om du vill testa flera kvantiseringar |
| **macOS** | macOS 14 Sonoma | macOS 15 eller senare |

**Tumregel:** Q4-bygget av 12B-modellen väger ~7–9 GB och behöver ~16 GB minne för att köras bekvämt. Har du bara 16 GB totalt — stäng tunga appar (Chrome, Docker) medan du kör.

---

## Väg 1 — Ollama (enklast, rekommenderas)

Ollama är det snabbaste sättet att komma igång. Den exponerar dessutom ett **OpenAI-kompatibelt API** på `localhost:11434` som du kan koppla andra verktyg mot.

### 1. Installera Ollama

```bash
# Via Homebrew
brew install ollama

# …eller ladda ner appen från https://ollama.com/download
```

Starta tjänsten (om du installerade via Homebrew):

```bash
ollama serve
```

### 2. Hämta och kör modellen

```bash
ollama pull gemma4:12b
ollama run gemma4:12b
```

Första gången laddas ~7–9 GB ner. Sen får du en chattprompt direkt i terminalen. Ollama väljer automatiskt `Q4_K_M`-kvantisering, vilket är den praktiska standarden.

### 3. Begränsa kontext om minnet tryter

På en 16 GB-Mac kan du minska minnesanvändningen genom att korta kontextfönstret:

```bash
ollama run gemma4:12b --num-ctx 4096
```

### 4. Använd API:t från egen kod

```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemma4:12b",
    "messages": [{"role": "user", "content": "Förklara kvantisering enkelt"}]
  }'
```

Eftersom API:t är OpenAI-kompatibelt funkar det rakt av med t.ex. OpenAI:s Python-/TS-bibliotek — peka bara `base_url` mot `http://localhost:11434/v1`.

---

## Väg 2 — LM Studio (grafiskt gränssnitt)

Vill du ha ett GUI i stället för terminal — t.ex. för att enkelt testa bild- och ljudinmatning — är LM Studio bäst.

1. Ladda ner LM Studio: [lmstudio.ai](https://lmstudio.ai)
2. Sök efter **`gemma-4-12B-it`** i modellsökningen.
3. Välj GGUF-bygget från **`lmstudio-community/gemma-4-12B-it-GGUF`** (eller `unsloth/gemma-4-12b-it-GGUF`).
4. Välj en **Q4_K_M**-variant för 16 GB-Mac, eller **Q8** om du har 32 GB+ och vill ha högre kvalitet.
5. Klicka **Download → Load**, så är du igång med ett par klick.

LM Studio kan också starta en lokal OpenAI-kompatibel server, precis som Ollama.

---

## Väg 3 — MLX / Google AI Edge (avancerat, mest Apple-optimerat)

För maximal prestanda på Apple Silicon kan du köra modellen direkt via Apples **MLX**-ramverk eller Googles **LiteRT-LM** (Google AI Edge).

**MLX:**

```bash
pip install mlx-lm
mlx_lm.generate --model google/gemma-4-12B-it --prompt "Hej!"
```

MLX kör beräkningarna direkt på Apples GPU/Neural Engine via unified memory och ger ofta bäst tokens/sekund på Mac.

**LiteRT-LM (Google AI Edge):** Färdigt deploybart bygge finns på Hugging Face som `litert-community/gemma-4-12B-it-litert-lm` — avsett för Googles AI Edge-runtime och agentiska lokala arbetsflöden.

---

## Snabbval

- **Bara vill chatta / koppla verktyg mot ett lokalt API** → Ollama (Väg 1)
- **Vill ha knappar och dra-och-släpp bilder/ljud** → LM Studio (Väg 2)
- **Vill ha maximal prestanda eller bygga egen app** → MLX / AI Edge (Väg 3)

---

## Vanliga problem

- **"Out of memory" / extremt långsamt:** Minnet räcker inte. Korta kontexten (`--num-ctx 4096`), stäng tunga appar, eller använd en mindre kvantisering.
- **Nedladdningen avbryts:** Kör `ollama pull gemma4:12b` igen — den återupptar.
- **Vill testa en lättare modell först:** Det finns mindre Gemma 4-varianter (t.ex. E2B/E4B) om 12B är för tungt för din Mac.

---

## Källor

- [Introducing Gemma 4 12B — Google Blog](https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemma-4-12b/)
- [Gemma 4 — Google DeepMind](https://deepmind.google/models/gemma/gemma-4/)
- [Bringing Gemma 4 12B to your Laptop — Google Developers Blog](https://developers.googleblog.com/bringing-gemma-4-12b-to-your-laptop-unlocking-local-agentic-workflows-with-google-ai-edge/)
- [google/gemma-4-12B-it — Hugging Face](https://huggingface.co/google/gemma-4-12B-it)
- [lmstudio-community/gemma-4-12B-it-GGUF — Hugging Face](https://huggingface.co/lmstudio-community/gemma-4-12B-it-GGUF)
- [litert-community/gemma-4-12B-it-litert-lm — Hugging Face](https://huggingface.co/litert-community/gemma-4-12B-it-litert-lm)
- [Running Gemma 4 with Ollama on macOS Apple Silicon — Medium](https://medium.com/@manyi.yim/running-gemma-4-with-ollama-on-mac-os-with-apple-silicon-a-step-by-step-guide-291063c2e8ca)
- [Google launches Gemma 4 12B — Slashdot](https://hardware.slashdot.org/story/26/06/03/1849210/google-launches-gemma-4-12b-ai-model-that-can-run-on-your-laptop)
