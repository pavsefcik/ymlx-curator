# ymlx-curator

The curated LLM list for [ymlx](https://github.com/pavsefcik/ymlx) — a standalone, always-up-to-date source of the models shown in ymlx's **Download new model** menu.

`ymlx-curator.md` replaces the copy of `curated-llms.md` bundled inside ymlx. Because it lives in its own repo, the list can be kept current even when ymlx itself isn't updated: at every startup, ymlx fetches the latest list from this repository on GitHub.

## How it works

- [ymlx-curator.md](ymlx-curator.md) is the single source of truth for curated models.
- ymlx pulls the latest version of this file from GitHub on every launch, so the model menu always reflects the newest entries.
- The list is filtered at runtime by ymlx to the machine's RAM tier and models already installed.

## File format

Blank-line-separated 2-line blocks under a tier header. The first line is the HuggingFace id used for downloading, and the second is the tag list shown in the menu.

```
8 GB RAM Tier Models

mlx-community/Qwen3.5-4B-MLX-4bit
vision, reasoning

mlx-community/gemma-4-e4b-it-4bit
vision, audio


16 GB RAM Tier Models

...
```

Tier headers are any line matching `GB RAM` (e.g. `if 16 GB RAM:`). See the ymlx README for how tiers map to RAM (≤ 8 GB, 16 / 18 GB, ≥ 24 GB).

## Contributing

To add, remove, or re-tag a model, edit [ymlx-curator.md](ymlx-curator.md) and open a pull request. Keep the 2-line block format intact.