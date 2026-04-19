# Next Step in Life

**An AI-powered A/B test of possible futures.**

A demo service for *AI기반 비즈니스 진화 — 전략 및 실습* (Prof. Jisoo Yi).

---

## The idea in one line

> Answer 15 honest questions about your life. Meet two versions of your future self. Watch them argue. Get a researched, actionable recommendation for the next 90 days.

## Why it's worth building

Most life-advice products fall into two traps: horoscope-vibe generators that say nothing, or long-form coaching that nobody finishes. This sits in between — it uses an LLM's ability to hold two personas simultaneously to surface the **truth you already half-know but haven't said out loud**, then grounds the recommendation with real web research and shippable next steps.

The killer feature isn't the quiz or the result page. It's the **debate between the two futures** — that's the emotional hook that makes people share it.

## The three stages

| Stage | What it does | LLM role |
|-------|--------------|----------|
| **1 · Quiz** | 15 honest questions: age, income, MBTI, concerns, dreams, strengths, what makes you sad. | Interprets free-text answers; extracts a life-trajectory vector. |
| **2 · Two Futures** | Renders two Ghibli-style persona cards — alternate 1-year futures based on the pivot question hidden in your answers. | Generates persona names, scenario, visual prompts, and initial vitals. |
| **3 · Debate → Verdict → Plan** | The personas have a ~20-message conversation that lands on a core insight. Then: a specific recommendation + deep-researched supporting stats + a concrete 90-day plan with real links. | Runs a two-agent conversation loop, then a web-research tool call for citations, then a plan-generation pass. |

## Demo

Open `next-step-in-life.html` in any modern browser. No build step, no API key needed — the LLM outputs are pre-written so teammates can experience the full flow end-to-end.

> Tip: try clicking straight through the quiz without typing anything. The demo backfills realistic answers (Sarah Kim, 28, burnt-out marketing manager) so the narrative still plays out.

## Tech stack (planned for the real build)

- **Frontend**: Next.js + Tailwind (static site on Vercel / GitHub Pages)
- **LLM**: Claude Sonnet 4.6 via Anthropic API for persona generation + debate loop
- **Web research**: a single tool-use loop that pulls 3–5 sources for stat citations
- **State**: no auth, no DB — everything client-side. If we want "share your result," lean on a signed URL with embedded JSON.
- **Image generation**: stable-diffusion XL with a fine-tuned Ghibli LoRA for persona art (or static SVGs like in the demo to keep it cheap)

## Suggested team split (4 people)

1. **Product / UX + narrative design** — writes the quiz, persona templates, debate script structure
2. **Frontend** — Next.js app, animations, persona card visuals
3. **LLM + research** — prompt engineering for persona + debate + web research tool use
4. **Integration + launch** — GitHub repo, CI, GH Pages deploy, analytics, sharing flow

## Why this is good for the class

- Hits all three vibe-coding pillars: creative product concept, multi-agent LLM design, shipped artifact.
- Easy to scope up (auth, history, share pages) or down (single HTML page) — good for 4 weeks.
- Visual + emotional + shareable → makes for a strong final presentation demo.

## Open questions for the team

- Do we constrain to a persona-pair taxonomy (career pivot, relationship, city move, break) or let the LLM decide freely?
- How many citations before diminishing returns? 3 feels right in the demo.
- Do we localize Korean first or English first? (The quiz has a Seoul flavor baked in.)

---

*This demo was built as a pitch artifact to propose the topic to our team of 4.*
