# Claude Code in Spanish, no fluff

[Leer en español](README.md)

Three files to make Claude Code always answer in Spanish and without filler: the `language` setting, the Concise output style, a language rule for CLAUDE.md against drifting into English (issue #96326) and an optional custom style, "Español directo".

The explanation of each piece and its limits is in the recipe:

- English: https://ctrlia.dev/en/recetas/claude-code-espanol.html
- Español: https://ctrlia.dev/recetas/claude-code-espanol.html

## What's inside

| File | Where it goes |
| --- | --- |
| `settings.json` | Its two keys (`language` and `outputStyle`) in `~/.claude/settings.json` |
| `claude-md-idioma.md` | Paste it into `~/.claude/CLAUDE.md` |
| `output-styles/espanol-directo.md` | Optional: `~/.claude/output-styles/espanol-directo.md` |

The CLAUDE.md rule and the style are written in Spanish on purpose: they are meant for people who want Claude Code to answer in Spanish.

## How to use it

```bash
# If you do not have ~/.claude/settings.json yet:
cp settings.json ~/.claude/settings.json
# If you do, add "language": "spanish" and "outputStyle": "Concise" (capital C) by hand.

cat claude-md-idioma.md >> ~/.claude/CLAUDE.md

# Optional: the custom style
mkdir -p ~/.claude/output-styles
cp output-styles/espanol-directo.md ~/.claude/output-styles/
```

Restart Claude Code and check the active style:

```bash
claude -p "/output-style" < /dev/null
```

To use "Español directo" instead of Concise: `/output-style "Español directo"` inside the session.

None of these pieces guarantees Spanish 100% of the time: they are instructions for the model, not rules that always hold.

## What was tested

With Claude Code **2.1.316** on Linux and a clean configuration (temporary `CLAUDE_CONFIG_DIR`): with this `settings.json`, `claude -p "/output-style"` shows `Output style: Concise`, and the "Español directo" style appears in the list. The JSON is valid. The effect of `language` on answers could not be measured cleanly on our machine.

## License

MIT. See [LICENSE](LICENSE).

---
Part of **[Ctrl+IA](https://ctrlia.dev/en/)**: code with Claude Code like a pro. Made by Carlos P.
