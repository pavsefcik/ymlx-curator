# ymlx-curator

The curated LLM list for [ymlx](https://github.com/pavsefcik/ymlx) — a standalone, always-up-to-date source of the models shown in ymlx's **Download new model** menu.

`ymlx-curator.md` replaces the copy of `curated-llms.md` bundled inside ymlx. Because it lives in its own repo, the list can be kept current even when ymlx itself isn't updated: at every startup, ymlx fetches the latest list from this repository on GitHub.

## How it works

- [ymlx-curator.md](ymlx-curator.md) is the single source of truth for curated models.
- ymlx pulls the latest version of this file from GitHub on every launch, so the model menu always reflects the newest entries.
- The list is filtered at runtime by ymlx to the machine's RAM tier and models already installed.

## File format

Blank-line-separated 3-line blocks under a tier header:

1. **Title** — the friendly name shown in ymlx's **Download new model** menu. Start it with the model's country flag (e.g. 🇨🇳, 🇺🇸, 🇫🇷).
2. **Model id(s)** — the HuggingFace id used for downloading.
3. **Tags** — the tag list shown after the title (e.g. `t3, vision`).

```
8 GB RAM Tier Models

🇨🇳 Alibaba Qwen 3.5 4B
mlx-community/Qwen3.5-4B-MLX-4bit
t3, vision

🇺🇸 Google Gemma 4 E4B
mlx-community/gemma-4-e4b-it-4bit
t3, vision, audio


16 GB RAM Tier Models

...
```

Tier headers are any line matching `GB RAM` (e.g. `if 16 GB RAM:`). See the ymlx README for how tiers map to RAM (≤ 8 GB, 16 / 18 GB, ≥ 24 GB).

### Multi-model entries (the Ministral exception)

Ministral ships as **two separate models** — an *Instruct* and a *Reasoning* half. List both ids on the model line separated by ` & `:

```
🇫🇷 Mistral Ministral 3 8B
mlx-community/Ministral-3-8B-Instruct-2512-4bit & mlx-community/Ministral-3-8B-Reasoning-2512-4bit
t3, vision
```

When the model line contains ` & `, ymlx treats this specially:

- **Download** fetches both ids.
- The **downloaded-models menu** shows a single entry (`Ministral-3-8B-4bit`), not the two ids.
- **Toggle thinking** (tab) swaps between the Instruct and Reasoning halves — only one is ever loaded at a time.

Only Ministral-style pairs should use ` & `; ordinary single-model entries keep one id on line 2.

## Contributing

To add, remove, or retitle a model, edit [ymlx-curator.md](ymlx-curator.md) and open a pull request. Keep the 3-line block format intact, and use ` & ` only for the Ministral Instruct/Reasoning pair.