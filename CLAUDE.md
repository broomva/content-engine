# Content Engine

Full-stack AI content studio skill for the broomva workspace.

## Structure

```
content-engine/
├── SKILL.md                        # Orchestrator entry point
├── skills/
│   ├── content-engine-dna/         # Visual DNA Compiler
│   ├── content-engine-cinema/      # Cinematic Generation Layer
│   ├── content-engine-autopilot/   # Browser Orchestration
│   └── content-engine-loop/        # Content Loop + Distribution
├── knowledge/
│   ├── raw/                        # Immutable source material
│   ├── compiled/                   # LLM-compiled identity files
│   └── schema.md                   # Compilation rules
├── templates/                      # File templates
├── scripts/                        # Automation scripts
└── extensions/                     # Plugin directory
```

## Conventions

- **Compiled files** are Markdown with YAML frontmatter and tool-specific prompt sections
- **Raw assets** are never modified by the LLM — they are the source of truth
- **Provenance** — every compiled file traces back to its raw sources
- **Tool-specific prompts** — each compiled file contains prompt fragments for Nano Banana, Soul Cinema, Weavy, etc.

## Dependencies

- Required: ffmpeg, GEMINI_API_KEY, FAL_KEY
- Optional: Topaz Gigapixel, ComfyUI, agent-browser
- Compounds: /content-creation, /blog-post, /social-intelligence, /brainrot-for-good, /brand-icons

## Design Spec

`~/broomva/docs/superpowers/specs/2026-04-07-content-engine-design.md`

## Linear Project

Content Engine project in Broomva workspace: BRO-547 through BRO-575
