# Set Claude Code's answer language, no fluff

[Leer en español](README.md) · The Spanish version is at the repo root and in [README.md](README.md); the English files are in `en/`.

Three files to make Claude Code always answer in the language you choose and without filler: the `language` setting, the Concise output style, a language rule for CLAUDE.md against drifting into another language after reading text in it (issue #96326) and an optional custom style, "Straight to the point". The examples in `en/` use English; the same setup works for any language: replace "english"/"English" with yours.

The explanation of each piece and its limits is in the recipe:

- English: https://ctrlia.dev/en/recetas/claude-code-espanol.html
- Español: https://ctrlia.dev/recetas/claude-code-espanol.html

## What's inside

| File | Where it goes |
| --- | --- |
| `en/settings.json` | Its two keys (`language` and `outputStyle`) in `~/.claude/settings.json` |
| `en/claude-md-language.md` | Paste it into `~/.claude/CLAUDE.md` |
| `en/output-styles/straight-to-the-point.md` | Optional: `~/.claude/output-styles/straight-to-the-point.md` |

## How to use it

```bash
cd ctrlia-claude-code-espanol/en
# If you do not have ~/.claude/settings.json yet:
cp settings.json ~/.claude/settings.json
# If you do, add "language": "english" and "outputStyle": "Concise" (capital C) by hand.

cat claude-md-language.md >> ~/.claude/CLAUDE.md

# Optional: the custom style
mkdir -p ~/.claude/output-styles
cp output-styles/straight-to-the-point.md ~/.claude/output-styles/
```

For another language, change `"english"` in `settings.json` (the value is passed as-is to Claude and not validated, so any name it understands works) and "English" in the CLAUDE.md rule and the style.

Restart Claude Code and check the active style:

```bash
claude -p "/output-style" < /dev/null
```

To use "Straight to the point" instead of Concise: `/output-style "Straight to the point"` inside the session.

None of these pieces guarantees the language 100% of the time: they are instructions for the model, not rules that always hold.

## What was tested

With Claude Code **2.1.316** on Linux and a clean configuration (temporary `CLAUDE_CONFIG_DIR`), with the Spanish version of these files: `claude -p "/output-style"` shows `Output style: Concise`, and the custom style appears in the list. The English files have the same structure and their JSON is valid, but they were not run separately. The effect of `language` on answers could not be measured cleanly on our machine.

## License

MIT. See [LICENSE](LICENSE).

---
Part of **[Ctrl+IA](https://ctrlia.dev/en/)**: code with Claude Code like a pro. Made by Carlos P.
