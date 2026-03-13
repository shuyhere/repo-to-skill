# Repo to Skill 🛠️

**Turn any GitHub repo into an agent skill.** Give it a repo URL — get back a tested, ready-to-use skill that teaches AI agents how to use that tool.

> Make any open-source repo an agent's claw. 🐾

## Why?

There are thousands of amazing open-source tools, but AI agents don't know how to use most of them well. This skill bridges the gap — it reads a repo's code, docs, and examples, then generates a complete skill that any agent can load and use immediately.

## How it works

```
GitHub Repo → Clone & Analyze → Generate Skill → Test → Evaluate → Ready to use
```

1. **Clone & Analyze** — Reads README, docs, examples, CLI help, entry points
2. **Classify** — Determines if it's a CLI tool, library, framework, or service
3. **Generate** — Creates SKILL.md + references + scripts
4. **Test** — Installs the tool and runs smoke tests
5. **Evaluate** — Benchmarks with-skill vs baseline on realistic prompts

## Install

```bash
npx skills add shuyhere/repo-to-skill
```

Or clone this repo and copy the skill folder into your agent's skills directory.

## Usage

### Slash command
```
/skill repo-to-skill https://github.com/vllm-project/vllm
```

### Natural language
> Create a skill for using https://github.com/hiyouga/LLaMA-Factory

### What you get

```
<tool-name>/
├── SKILL.md              # How to use the tool (under 500 lines)
├── references/           # Detailed docs, loaded on demand
├── scripts/              # Setup & helper scripts
└── evals/
    └── evals.json        # Test cases with assertions
```

## Example

Generated a **LlamaFactory skill** from [hiyouga/LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory):
- Covers installation, LoRA/QLoRA/DPO training, dataset prep, multi-GPU, deployment
- Scored **22/22 (100%)** on all eval assertions
- Baseline without skill: 21/22 (95.5%)

## Included tools

| File | Purpose |
|------|---------|
| `SKILL.md` | Core skill — the 6-step generation process |
| `scripts/analyze_repo.sh` | Automated repo analyzer |
| `references/skill-format.md` | Skill format reference |
| `references/eval-schemas.md` | Eval & benchmark JSON schemas |

## Compatible with

- [OpenClaw](https://github.com/openclaw/openclaw)
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Codex](https://openai.com/codex)
- Any agent supporting the [Agent Skills](https://agentskills.io) format

## License

MIT
