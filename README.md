# Claude Code en español y sin relleno

[Read in English](README.en.md)

Tres archivos para que Claude Code te responda siempre en español y sin paja: el ajuste `language`, el estilo de salida Concise, una regla de idioma para CLAUDE.md contra la deriva al inglés (issue #96326) y un estilo propio opcional, «Español directo».

La explicación de cada pieza y sus límites está en la receta:

- Español: https://ctrlia.dev/recetas/claude-code-espanol.html
- English: https://ctrlia.dev/en/recetas/claude-code-espanol.html

## Qué incluye

| Archivo | Dónde va |
| --- | --- |
| `settings.json` | Sus dos claves (`language` y `outputStyle`) en `~/.claude/settings.json` |
| `claude-md-idioma.md` | Pégalo en `~/.claude/CLAUDE.md` |
| `output-styles/espanol-directo.md` | Opcional: `~/.claude/output-styles/espanol-directo.md` |

## Cómo usarlo

```bash
# Si aún no tienes ~/.claude/settings.json:
cp settings.json ~/.claude/settings.json
# Si ya lo tienes, añade a mano "language": "spanish" y "outputStyle": "Concise" (con C mayúscula).

cat claude-md-idioma.md >> ~/.claude/CLAUDE.md

# Opcional: el estilo propio
mkdir -p ~/.claude/output-styles
cp output-styles/espanol-directo.md ~/.claude/output-styles/
```

Reinicia Claude Code y comprueba el estilo activo:

```bash
claude -p "/output-style" < /dev/null
```

Para usar «Español directo» en lugar de Concise: `/output-style "Español directo"` dentro de la sesión.

Ninguna de estas piezas garantiza el español al 100 %: son instrucciones para el modelo, no reglas que se cumplan siempre.

## Qué se probó

Con Claude Code **2.1.316** en Linux y una configuración limpia (`CLAUDE_CONFIG_DIR` temporal): con este `settings.json`, `claude -p "/output-style"` muestra `Output style: Concise`, y el estilo «Español directo» aparece en la lista. El JSON es válido. El efecto de `language` en las respuestas no se pudo medir de forma limpia en nuestro equipo.

## Licencia

MIT. Ver [LICENSE](LICENSE).

---
Parte de **[Ctrl+IA](https://ctrlia.dev/)**: programa con Claude Code como un pro, en español. Hecho por Carlos P.
