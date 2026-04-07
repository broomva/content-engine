---
name: content-engine
description: "Full-stack AI content studio — orchestrates visual DNA compilation, cinematic generation, browser-automated tool execution, and multi-platform distribution into a unified content pipeline. Compiles brand identity, character sheets, and style guides into persistent knowledge (Karpathy compile-then-query pattern), then generates premium cinematic content using Nano Banana, Soul Cinema, Weavy, Veo 3.1, and ComfyUI with consistent character identity and intentional visual direction. Triggers on: 'content engine', 'generate campaign', 'compile brand', 'cinematic content', 'AI content studio', 'batch generate', 'content pipeline', 'visual DNA', 'character consistency'."
---

# Content Engine

Full-stack AI content studio: compile visual identity once, generate premium content at scale, distribute everywhere.

```
COMPILE → GENERATE → POST-PRODUCE → DISTRIBUTE → MEASURE → REFINE
```

## Commands

| Command | What it does |
|---------|-------------|
| `/content-engine compile` | Raw assets → compiled visual DNA (brand, character, style) |
| `/content-engine lint` | Health-check compiled knowledge for consistency |
| `/content-engine generate` | Create content using compiled identity + scene brief |
| `/content-engine autopilot setup {tool}` | Save browser session for a generation tool |
| `/content-engine autopilot run` | Batch generation via browser automation |
| `/content-engine campaign {brief}` | Full pipeline: compile → generate → distribute |
| `/content-engine loop` | Compound existing skills for distribution |

## Architecture

Four sub-skills, each handling one layer:

```
[content-engine-dna]       Visual DNA Compiler
        ↓                  raw/ → compiled/ (brand DNA, character sheets, style guides)
[content-engine-cinema]    Cinematic Generation Layer
        ↓                  compiled identity → tool-specific prompts → generation
[content-engine-autopilot] Browser Orchestration
        ↓                  Playwright drives tools OR API calls → organized output
[content-engine-loop]      Content Loop + Distribution
                           compounds /blog-post + /content-creation + /social-intelligence
```

## Quick Start

### 1. Compile Brand Identity

Drop reference assets into `knowledge/raw/`:
- Brand campaign photos → `knowledge/raw/brand-assets/`
- Character face references → `knowledge/raw/character-refs/`
- Style inspiration (mood boards, reference reels) → `knowledge/raw/style-inspiration/`

Then compile:
```
/content-engine compile
```

This analyzes all raw assets via Gemini multimodal and produces compiled identity files in `knowledge/compiled/` with tool-specific prompt fragments.

### 2. Generate Content

Write a scene brief or use a campaign plan:
```
/content-engine generate --brand acme --character luna --scenes 5 --format reels
```

The engine:
1. Reads compiled identity (brand DNA + character sheet + style guide)
2. Selects the best tool per the tool priority matrix
3. Injects compiled identity into tool-specific prompts
4. Generates via API (fal.ai, @google/genai) or browser automation
5. Runs post-production (upscale → grade)
6. Organizes output with manifest.json tracking

### 3. Run a Full Campaign

```
/content-engine campaign "Mediterranean lifestyle, 10 summer scenes, golden hour, reels + carousel"
```

Orchestrates all four skills end-to-end: compile (if needed) → generate scenes → post-produce → adapt for platforms → distribute.

### 4. Distribute

```
/content-engine loop
```

Compounds existing skills for multi-platform distribution:
- `/blog-post` — Writing + 6 platform adaptations
- `/content-creation` — TTS, Remotion video, media pipeline
- `/social-intelligence` — Distribution + engagement monitoring
- `/brainrot-for-good` — High-retention short-form video
- `/brand-icons` — OG images, social cards

## Setup & Prerequisites

### Required

```bash
# Check prerequisites
echo "=== Required ==="
which ffmpeg && echo "ok ffmpeg" || echo "MISSING: brew install ffmpeg"
echo ""
echo "=== API Keys ==="
[ -n "$GEMINI_API_KEY" ] && echo "ok GEMINI_API_KEY" || echo "MISSING: needed for Gemini analysis + Veo 3.1"
[ -n "$FAL_KEY" ] && echo "ok FAL_KEY" || echo "MISSING: needed for Nano Banana 2, Kling via fal.ai"
echo ""
echo "=== Browser Automation ==="
which agent-browser && echo "ok agent-browser" || echo "MISSING: needed for autopilot mode"
```

### Optional (enhance quality)

- **Topaz Gigapixel AI** — CLI upscaling (falls back to Real-ESRGAN)
- **ComfyUI** — Local node-based pipelines with LoRA style-locking
- **Higgsfield account** — Soul Cinema start frames
- **Weavy account** — Scene variation with character consistency
- **Artlist.io** — AI-powered music matching

### Tool Session Setup

For browser-automated tools, run setup once per tool:
```
/content-engine autopilot setup higgsfield
/content-engine autopilot setup weavy
```

This launches Chrome, you log in manually, and the session is saved for future automated use.

## Knowledge Architecture

### Karpathy Compile-Then-Query Pattern

```
knowledge/
├── raw/              # Immutable source material (never modified by LLM)
│   ├── brand-assets/     # Campaign photos, logos, style guides
│   ├── character-refs/   # Face photos, pose references
│   ├── style-inspiration/# Mood boards, reference reels
│   └── scene-briefs/     # Scene descriptions
├── compiled/         # LLM-compiled identity files (the "wiki")
│   ├── brands/           # Per-brand DNA (.md)
│   ├── characters/       # Per-character sheets (.md)
│   └── styles/           # Compiled style guides (.md)
└── schema.md         # Compilation rules + templates
```

**raw/** is source code. **compiled/** is executable. The LLM is the compiler.

Every compiled file:
- Traces provenance to raw sources
- Contains tool-specific prompt fragments
- Is human-reviewable Markdown
- Gets actively maintained via lint

### Mapping to Existing Patterns

| Content Engine | Karpathy Wiki | MemPalace | Broomva Knowledge Graph |
|---------------|--------------|-----------|----------------------|
| `raw/` | `raw/` | — | Layer 2 (raw extracts) |
| `compiled/` | `wiki/` | Rooms/Closets | Layer 3 (entity pages) |
| `schema.md` | `CLAUDE.md` | Wings/Halls | CLAUDE.md |
| Feedback loop | Linting pass | Tunnels | Layer 4 (synthesis) |

## Tool Priority Matrix

| Task | Best Tool | Fallback | API? |
|------|-----------|----------|------|
| Cinematic start frame | Soul Cinema (Higgsfield) | Nano Banana Pro | Yes |
| Character consistency | Nano Banana Pro | SD + LoRA | Yes (fal.ai) |
| Multi-angle generation | Nano Banana 2 | Weavy | Yes (fal.ai) |
| Scene variation | Weavy | Nano Banana + scene prompt | Browser |
| Video from keyframe | Veo 3.1 / Seedance 2.0 | Kling | Yes |
| Motion transfer | Kling | Wan | Browser + ComfyUI |
| Upscaling | Topaz Gigapixel | Real-ESRGAN | CLI |
| Color grading | Lightroom | ffmpeg LUT | CLI/Browser |
| AI music | Artlist.io | Suno | Browser |
| Intent captions | OpenCaptions | ffmpeg burn-in | CLI (future) |

## Generation Modes

**Mode 1: API-First** (fastest, programmatic)
- fal.ai → Nano Banana 2, Kling, Veo
- @google/genai → Veo 3.1, Gemini image
- Direct calls from Claude Code, no browser needed

**Mode 2: Browser-Automated** (tools without APIs)
- Playwright drives Weavy, Higgsfield Studio, Artlist
- Auth persisted via saved session state
- Batch generation with organized output

**Mode 3: Local Pipeline** (maximum control)
- ComfyUI + Stable Diffusion + LoRA
- Full node-based control over every generation step
- Topaz CLI for upscaling

## Output Organization

```
output/{campaign-slug}/
├── raw/          # Direct generation output
├── upscaled/     # After Topaz/Real-ESRGAN pass
├── graded/       # After color grading
└── manifest.json # Prompts, identity refs, tool used, timestamps
```

## Extension Points

Extensions live in `extensions/`. Each extension:
- Has its own SKILL.md declaring which pipeline stage it hooks into
- Hook points: pre-generation, post-generation, post-production, distribution
- Can read from `compiled/` but only writes to its own output namespace
- Registered in `extensions/README.md`

### Planned Extensions
- **OpenCaptions** — Intent-driven captions (post-production hook)
- **ComfyUI MCP** — Direct tool calls for node pipelines
- **LoRA Training** — Compiled DNA as training data for custom models

## Compounding Skills

This skill compounds on the existing broomva content ecosystem:

| Skill | Role |
|-------|------|
| `/content-creation` | Media pipeline (Nano Banana, Veo 3.1, TTS, Remotion) |
| `/blog-post` | Writing + 6 platform adaptations + publish.sh |
| `/social-intelligence` | Engagement loop + knowledge extraction |
| `/brainrot-for-good` | High-retention short-form video |
| `/brand-icons` | OG images, social cards |
| `/agent-browser` | Playwright browser automation |
| `/arcan-glass` | Brand styling tokens |

## Research Sources

Built from analysis of:
- **viznfr** — Claude Code + Playwright autopilot, Nano Banana character sheets, brand DNA extraction
- **ohneis652** — ComfyUI node pipelines, LoRA style-locking, Soul Cinema start-frame doctrine, 25 design styles
- **Vidis AI / Skool3** — ReelEngine/PromptEngine, character consistency, motion control, monetization
- **MemPalace** — Spatial hierarchy, AAAK compression, MCP-native memory
- **Karpathy LLM Wiki** — raw/wiki/schema 3-layer architecture, compile-then-query, active linting
