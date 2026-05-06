# rech.studio Plugins für Claude Code

Plugin-Marketplace von [rech.studio](https://rech.studio) für [Claude Code](https://docs.claude.com/claude-code) — KI-gestützte Workflows für B2B-Teams.

Dieses Repository ist **kein Plugin selbst**, sondern der Katalog. Die eigentlichen Plugins liegen in eigenen Repos und werden hier nur referenziert.

## Verfügbare Plugins

| Plugin | Beschreibung | Plugin-Repo |
|---|---|---|
| `ki-vertriebsteam` | Skills und Agents für einen KI-gestützten B2B-Vertriebs-Workflow — Prospecting, Qualifizierung, Outreach, Proposals, Follow-up. | [jonasrech/ki-vertriebsteam-claude](https://github.com/jonasrech/ki-vertriebsteam-claude) |

## Installation

Du brauchst eine aktuelle Version von [Claude Code](https://docs.claude.com/claude-code) (CLI, VS Code oder JetBrains).

**1. Marketplace hinzufügen** (einmalig):

```bash
/plugin marketplace add jonasrech/rech-studio-plugins
```

**2. Plugin installieren:**

```bash
/plugin install ki-vertriebsteam@rech-studio
```

Danach stehen die Skills als Slash-Commands zur Verfügung, z. B. `/ki-vertriebsteam:sales-prep` oder `/ki-vertriebsteam:sales-objections`.

## Updates

Wenn ein Plugin aktualisiert wird, hol dir die neue Version mit:

```bash
/plugin marketplace update rech-studio
/plugin update ki-vertriebsteam
```

## Plugin entfernen

```bash
/plugin uninstall ki-vertriebsteam
```

Den kompletten Marketplace entfernen:

```bash
/plugin marketplace remove rech-studio
```

## Wie ist das hier aufgebaut?

```
rech-studio-plugins/
├── .claude-plugin/
│   └── marketplace.json   ← Katalog: listet alle rech.studio-Plugins
├── README.md
└── LICENSE
```

Die `marketplace.json` ist ein reines Verzeichnis. Jeder Eintrag verweist auf ein eigenes Plugin-Repository — die Plugins selbst werden dort gepflegt und versioniert, nicht hier.

## Für Entwickler:innen — wie kommt ein neues Plugin in den Marketplace?

1. Plugin-Repo auf GitHub anlegen (z. B. `jonasrech/rech-studio-marketing`) mit `.claude-plugin/plugin.json` + Skills/Agents/Hooks. Mit `git tag v0.1.0` taggen.
2. Eintrag in [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) ergänzen:
   ```json
   {
     "name": "rech-studio-marketing",
     "source": {
       "source": "github",
       "repo": "jonasrech/rech-studio-marketing",
       "ref": "v0.1.0"
     },
     "description": "...",
     "category": "productivity",
     "license": "MIT",
     "homepage": "https://rech.studio",
     "strict": true
   }
   ```
3. Commit, push.
4. Bestehende Nutzer:innen sehen das neue Plugin nach `/plugin marketplace update rech-studio`.

Bei jedem neuen Plugin-Release das `ref` in der `marketplace.json` auf den neuen Tag bumpen, damit Updates ausgerollt werden.

## Hinweis zur aktuellen Version

Der `ref` ist im aktuellen `ki-vertriebsteam`-Eintrag bewusst nicht gesetzt — der Marketplace verfolgt zunächst den `main`-Branch des Plugin-Repos. Sobald das Plugin-Repo seinen ersten stabilen Release-Tag (`v0.1.0`) hat, wird der Eintrag um `"ref": "v0.1.0"` ergänzt, damit Updates kontrolliert ausgerollt werden.

## Lizenz

[MIT](./LICENSE) — Copyright (c) 2026 Jonas Rech / rech.studio ([https://www.rech.studio](https://www.rech.studio))
