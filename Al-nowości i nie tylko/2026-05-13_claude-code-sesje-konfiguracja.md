---
title: "Claude Code — konfiguracja vaultu (2026-05-13)"
date: 2026-05-13
tags:
  - tool
  - project
---

# Claude Code — konfiguracja vaultu

Dzisiaj przeprowadziłem pełną konfigurację vaultu Obsidian przez [[Claude Code]]. Poniżej zapis wszystkich sesji.

## Chronologia sesji

### 15:13 — Inicjalizacja (`/init`)

Uruchomiono komendę `/init`, która przeanalizowała vault i wygenerowała `CLAUDE.md` — plik konfiguracyjny dla przyszłych instancji Claude Code. Plik dokumentuje:

- strukturę folderów vaultu
- schemat YAML notatek YouTube
- reguły Mermaid mindmap (ściśle wymagane przez Obsidian)
- pluginy: [[Copilot]], obsidian-git, smart-connections

W tej samej sesji zainstalowano plugin **obsidian-show-hidden-files** (release 2.5.0) — pozwala na wyświetlanie ukrytych plików w Obsidian.

### 15:49 — Urwana sesja

Próba pobrania `kepano/obsidian-skills` — sesja urwała się w trakcie klonowania repo. Brak efektu.

### 16:00 — Instalacja Obsidian Skills

Pomyślna instalacja 5 skilli z `kepano/obsidian-skills` do `.claude/skills/`:

| Skill | Co robi |
|-------|---------|
| `obsidian-markdown` | Obsidian Flavored Markdown — wikilinki, callouts, frontmatter |
| `obsidian-bases` | Pliki `.base` z widokami, filtrami i formułami |
| `json-canvas` | Pliki `.canvas` — wizualne mapy i diagramy |
| `obsidian-cli` | Interakcja z vaultem przez CLI |
| `defuddle` | Ekstrakcja czystego Markdown ze stron www |

### 16:00–20:47 — Instalacja claude-code-obsidian

Pobrano i zainstalowano repozytorium `Szewowsky/claude-code-obsidian`:

- komenda `/setup` → dostępna jako slash command
- `.claude/CLAUDE.md` → reguły pracy z vaultem (persona Rafał, język polski, struktura folderów, tagowanie, git workflow)
- `tags.md` → starter kit tagów

### 20:59 — Przeglądanie logów sesji

Przeglądanie i analiza plików `.jsonl` z logami wszystkich poprzednich sesji dnia. Logi przechowywane są w:

```
C:\Users\acer\.claude\projects\D--Obsydian-Sztuczna-inteligencja\
```

### 21:00+ — Konfiguracja Git i obsidian-git

Inicjalizacja git i podłączenie remote do GitHub:

- `git init` w katalogu vaultu
- remote: `https://github.com/ScalperTraders/Obsidian-copailot-backup.git`
- stworzony `.gitignore` wykluczający klucze API, cache, pliki binarne

**Pierwszy push** zablokowany przez GitHub Push Protection — `remotely-save/main.js` zawierał hardkodowane Google OAuth credentials (wbudowane w kod pluginu). Plugin wykluczono z gita.

Skonfigurowano `obsidian-git/data.json`:
- auto-commit + auto-push co **10 minut**
- pull przy starcie Obsidian
- pull przed każdym pushem

**Efekt:** obsidian-git wykrył repo i od razu wykonał pierwszy automatyczny backup (commit `ea6c5ab`).

```
git log:
3a37a86  config: obsidian-git — auto-push co 10 min
ea6c5ab  vault backup: 2026-05-13 22:32:42  ← pierwszy auto-backup
40c9e19  init: konfiguracja vaultu Obsidian z Claude Code
```

## Struktura konfiguracji Claude Code

```
.claude/
├── CLAUDE.md              # Reguły i persona dla Claude
├── commands/
│   └── setup.md           # Komenda /setup
└── skills/
    ├── obsidian-markdown/
    ├── obsidian-bases/
    ├── json-canvas/
    ├── obsidian-cli/
    └── defuddle/
```

## Wnioski

> [!insight] Claude Code jako narzędzie do zarządzania vaultem
> Konfiguracja przez Claude Code pozwala na automatyzację powtarzalnych zadań w Obsidian — tworzenie notatek według szablonów, instalacja pluginów, zarządzanie strukturą vaultu. Kluczowe jest dobre `CLAUDE.md`, które nadaje kontekst każdej nowej sesji.

> [!tip] Logi sesji
> Każda sesja Claude Code jest zapisywana jako plik `.jsonl` — można je odczytać i przeanalizować, żeby zobaczyć co dokładnie było robione. Przydatne do audytu i nauki.

> [!warning] GitHub Push Protection
> Pluginy Obsidian mogą zawierać hardkodowane sekrety (OAuth, API keys) w `main.js`. GitHub to wykryje i zablokuje push. Rozwiązanie: wykluczyć problematyczne pluginy z gita w `.gitignore`. Dotyczyło pluginu `remotely-save`.
