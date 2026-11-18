# Visual Styles Quick Reference

**MANDATORY: Every video production must declare a visual style at the `idea` stage.**

---

## Three Style Systems Available

| System | Count | Location | Use For |
|--------|-------|----------|---------|
| **HeyGen Prompt Styles** | 20 | `.agents/skills/create-video/references/visual-styles.md` | Quick HeyGen Video Agent prompts (copy-paste block) |
| **visual-style.md Files** | 5 | `.agents/skills/visual-style/references/gallery/` | Full design systems for HyperFrames/Remotion/Figma/HTML |
| **Style Playbooks (YAML)** | 5 | `styles/*.yaml` | Pipeline templated scenes (clean-professional, flat-motion-graphics, etc.) |

---

## HeyGen Prompt Styles (20) — Copy the STYLE block into your prompt

| # | Style | Designer | Mood | Best For |
|---|-------|----------|------|----------|
| 1 | **Soft Signal** | Sagmeister | Intimate, warm | Personal stories, wellness |
| 2 | **Warm Grain** | Eksell | Organic, friendly | Environmental, sustainability |
| 3 | **Quiet Drama** | Ray | Humanist, contemplative | Profiles, biographical |
| 4 | **Heritage Reel** | Cassandre | Nostalgic, vintage | History, retrospectives |
| 5 | **Silk Route** | Abedini | Flowing, mysterious | Global affairs, cross-cultural |
| 6 | **Swiss Pulse** | Müller-Brockmann | Clinical, precise | **Data-heavy, analytical** |
| 7 | **Geometric Bold** | Tanaka | Minimal, elegant | Lifestyle, visual essays |
| 8 | **Velvet Standard** | Vignelli | Premium, timeless | Luxury, investor updates |
| 9 | **Digital Grid** | Crouwel | Systematic, technical | Infrastructure, engineering |
| 10 | **Contact Sheet** | Brodovitch | Editorial, investigative | Journalism, deep dives |
| 11 | **Folk Frequency** | Terrazas | Cultural, vivid | Festivals, food, heritage |
| 12 | **Earth Pulse** | Ghariokwu | Grounded, communal | Community, grassroots |
| 13 | **Dream State** | Tomaszewski | Surreal, poetic | Op-eds, philosophy |
| 14 | **Play Mode** | Ahn Sang-soo | Playful, irreverent | Entertainment, pop culture |
| 15 | **Carnival Surge** | Lins | Euphoric, celebratory | Milestones, hype |
| 16 | **Shadow Cut** | Hillmann | Dark, cinematic | Exposés, investigations |
| 17 | **Deconstructed** | Brody | Industrial, raw | **Tech news, punk energy** |
| 18 | **Maximalist Type** | Scher | Loud, kinetic | Big announcements, launches |
| 19 | **Data Drift** | Anadol | Futuristic, immersive | **AI/tech, innovation** |
| 20 | **Red Wire** | Tartakover | Urgent, immediate | Breaking news, crisis |

**How to use:** Copy the code block under each style (e.g., `STYLE — SWISS PULSE...`) into your HeyGen Video Agent prompt's STYLE section.

---

## visual-style.md Files (5) — Full design systems with connectors

| File | Style | Key Traits |
|------|-------|------------|
| `mueller-brockmann-swiss.visual-style.md` | Swiss International | Grid-locked, B&W + electric blue, Helvetica only |
| `neville-brody-industrial.visual-style.md` | Industrial / Deconstructed | Dark grey, rust orange, angled type, glitch textures |
| `saul-bass-cinematic.visual-style.md` | Cinematic Titles | Bold shapes, film title cards, strong contrast |
| `game-boy-color.visual-style.md` | Pixel Art / Retro | 4-color palette, pixel aesthetic, scanlines |
| `heygen-ai-video.visual-style.md` | Modern AI/SaaS | Clean gradients, tech-forward, modern |

**How to use:** `Apply the visual-style skill: load <filename>.visual-style.md and use it for this composition` — connects to HeyGen, HTML Slides, Figma, paper.design.

---

## Style Playbooks (5) — YAML playbooks for templated pipelines

| Playbook | File | Best For |
|----------|------|----------|
| Clean Professional | `styles/clean-professional.yaml` | Corporate, educational, SaaS |
| Premium Minimalist | `styles/premium-minimalist.yaml` | Investor updates, expert explainers |
| Flat Motion Graphics | `styles/flat-motion-graphics.yaml` | Social media, TikTok, startups |
| Minimalist Diagram | `styles/minimalist-diagram.yaml` | Technical deep-dives, architecture |
| Anime Ghibli | `styles/anime-ghibli.yaml` | Narrative animations, nature, emotional |

**How to use:** Reference in pipeline manifest or brief: `playbook: "flat-motion-graphics"`.

---

## Mood-to-Style Quick Pick

| Content feels... | Try These First |
|------------------|-----------------|
| Personal, intimate | Soft Signal, Quiet Drama |
| Natural, earthy | Warm Grain, Earth Pulse |
| Nostalgic, historical | Heritage Reel |
| **Data-driven, analytical** | **Swiss Pulse, Digital Grid** |
| Elegant, premium | Velvet Standard, Geometric Bold |
| Cultural, global | Silk Route, Folk Frequency |
| Investigative, serious | Contact Sheet, Shadow Cut |
| Fun, lighthearted | Play Mode, Carnival Surge |
| Philosophical, abstract | Dream State |
| **Punk, raw, tech** | **Deconstructed** |
| Hype, high-energy | Maximalist Type, Carnival Surge |
| **Tech-forward, AI, futuristic** | **Data Drift** |
| Breaking, urgent | Red Wire |

---

## Agent Workflow (Rule Zero Addition)

When user asks for a video:

1. **Identify pipeline** → 2. **Preflight** → **3. Determine Visual Style (MANDATORY)** → 4. Execute stages

**At step 3, you MUST do one of:**
- Use a named HeyGen style (copy STYLE block)
- Apply a `.visual-style.md` file via `visual-style` skill
- Pick a style playbook from `styles/`
- Extract from reference video/URL using `visual-style` skill
- **Ask user:** Present 3 options from Mood-to-Style table, get approval

**Record in brief artifact:**
```json
{
  "visual_style": {
    "system": "heygen|visual-style-md|playbook|custom",
    "name": "Swiss Pulse",
    "source": "create-video/references/visual-styles.md"
  }
}
```

---

## No "Cartoon / 3D / Vector" Presets Exist

These systems don't have explicit cartoon/3D/vector presets. For those aesthetics:

- **Cartoon/flat vector:** Use `visual-style` skill to create custom: "Flat vector illustration, 3-color palette, clean lines, bold shapes"
- **3D/Pixar-style:** Use `visual-style` skill: "Pixar-style 3D, soft lighting, rounded forms, subsurface scattering"
- **Anime:** Use `anime-ghibli` playbook or create custom visual-style.md
- **Hand-drawn ink:** Use **Ink Theater** engine (`skills/creative/ink-theater.md`)

---

## Files to Read

- `.agents/skills/create-video/references/visual-styles.md` — Full 20 HeyGen styles with code blocks
- `.agents/skills/visual-style/SKILL.md` — How to create/extract/apply visual-style.md
- `.agents/skills/visual-style/references/gallery/` — 5 gallery files
- `styles/*.yaml` — 5 playbook YAML files
- `skills/meta/taste-direction.md` — For custom/atelier work