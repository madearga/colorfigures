# Colorfigures (mirror) — with a local figure example

A mirror of April Zhu's MIT-licensed **Colorfigures** skill, plus one figure I made with it.

> **Upstream / credit:** everything under `SKILL.md`, `assets/`, `scripts/` and the original `README.md` content is
> April Zhu's work — MIT licensed, see [LICENSE](LICENSE). Credits: built on
> [ISO-GLOW](https://isoglow.dev) by April Zhu, which is built on
> [iso-figure](https://github.com/MrBongoC/ai-iso-skill) by Tolga Cohce (MIT).
> My additions are only: `examples/how-llm-works.html` and the note below.

## What this skill does

Describe an everyday object in one line and the agent draws it hand-inked and isometric, as one
self-contained HTML file with buttons that actually work: real 3D bodies shaded in flat light, mid and
dark bands, a heavy ink silhouette with finer inner lines, a flat blue cast shadow, a hand-drawn wobble,
warm paper and body-colour swatches. Ask *how something works* and it labels the parts, lighting each
one up as it works.

Live examples: https://april-zhu.com/colorfigures-demo · Skill page: https://april-zhu.com/colorfigures

## Install

**Claude Code** — paste in Terminal, then restart Claude Code:

    mkdir -p ~/.claude/skills && curl -fsSL https://april-zhu.com/colorfigures/colorfigures.tar.gz | tar -xz -C ~/.claude/skills

**Pi / Hermes / any agent** — copy the `SKILL.md` + `assets/` + `scripts/` folders into that agent's
skills directory (e.g. `~/.pi/agent/skills/colorfigures/`, `~/.hermes/skills/colorfigures/`).

**Claude.ai** — download `colorfigures.skill` and upload it in Settings → Capabilities → Skills, then switch it on.

## Try

- a gumball machine where I can put in a coin and turn the crank
- a record player: put on a record, drop the needle and it plays
- a kettle that boils and clicks off by itself — show how it knows when to stop
- how does a toaster know when to pop? make it a Colorfigure

The agent saves an `.html` file. Open it in your browser and press things.

## What's inside

- `SKILL.md` — the instructions the agent follows
- `assets/core.js` — the engine: projection, 3D shapes and shading, ink, labels, the page with its buttons and controls
- `assets/examples/` — complete figures to learn from (vending machine, washing machine)
- `scripts/build.py` — makes one self-contained file: `python3 scripts/build.py figure.html OUT.html`
- `examples/how-llm-works.html` — **my addition:** an interactive isometric machine explaining how an LLM
  works (tokenizer slot → embedding rack → transformer tower with attention → softmax screen → sampling
  loop). Open it in a browser and press the buttons.

Plain text only. Nothing runs on install; figures run in the browser like any web page, with no outside requests.

## My example: How an LLM works

`examples/how-llm-works.html` is a single self-contained file — open it directly, no server needed.

Press the buttons in pipeline order:

1. **Type prompt** — "The cat…", "Once upon…" or "Jakarta…"
2. **Tokenize** — the slot chops the paper tape into tokens; each token flies to the embedding rack as a
   coloured cube (watch "Jakarta" split into `Ja` + `karta`, like real subword tokenizers)
3. **Forward pass** — the cubes ride up through the glass transformer tower; attention lines flash between
   tokens on each floor
4. **Sample next token** — the softmax screen shows candidate bars, the chosen token drops onto the output
   rail and **loops back** into the context window (the arrow on the board)
5. **Reset** — start over

Sampling is weighted-random, so the same prompt can produce different continuations.

## License

MIT. See [LICENSE](LICENSE).

Upstream author: April · [@Aprilzz423](https://x.com/Aprilzz423)
