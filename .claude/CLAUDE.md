# CLAUDE.md

Obsidian vault — Twój Second Brain zarządzany przez Claude Code.

## Persona

**Persona:** [Rafał — pasjonat AI, zainteresowany technologią i tradingiem"]

**Język:** Polski

**Data:** Używaj daty z system prompt do nazywania plików (YYYY-MM-DD_...) i kontekstu czasowego.

## Read Before Acting

Przed każdym zadaniem: **CZYTAJ istniejące pliki NAJPIERW**. Przed tworzeniem notatki → sprawdź czy podobna już istnieje. Przed tagowaniem → przeczytaj `tags.md`.

## Vault Structure

```
Al-nowości i nie tylko/   # Nowości AI i ogólne notatki
Linki/                    # Zapisane linki i zasoby
Trading/                  # Notatki o tradingu
Youtube/                  # Notatki z filmów YouTube
Zdrowie/                  # Notatki o zdrowiu
copilot/                  # Dane pluginu AI Copilot (nie edytuj ręcznie)

tags.md                   # Jedyne źródło prawdy dla tagów
```

## Formatting Rules

1. **Wikilinki**: Do linkowania notatek ZAWSZE używaj `[[podwójnych nawiasów]]`
2. **Kontekst relacyjny**: Tworzysz notatkę → sprawdź czy pojęcia mają istniejące notatki → linkuj je `[[tak]]`
3. **Tagowanie**: Tylko tagi z `tags.md`. Format: `#tag`. Nie wymyślaj nowych.
4. **Format**: Wyłącznie czysty Markdown (.md)
5. **Analiza wiedzy**: W raportach/analizach ZAWSZE linkuj pojęcia `[[wikilinkami]]` aby wpiąć raport w graf
6. **Concept notes**: Gdy identyfikujesz oryginalną myśl → linkuj do powiązanych notatek

## File Naming

- Notatki YouTube: `Youtube/YYYY-MM-DD_tytuł-notatki.md`
- Notatki AI: `Al-nowości i nie tylko/YYYY-MM-DD_temat.md`
- Linki: `Linki/YYYY-MM-DD_temat.md`

## Git Workflow

Po większych zmianach w vaultcie zaproponuj commit i push. Dotyczy to:
- dodania nowych notatek lub edycji wielu plików
- zmian w strukturze katalogów
- zmian w konfiguracji `.obsidian/` lub `.claude/`

**Nie wykonuj `git commit` ani `git push` automatycznie** — najpierw zaproponuj wiadomość commita i poczekaj na wyraźną zgodę.

## Self-Update

Gdy użytkownik powie "zaktualizuj CLAUDE.md":
1. Przeczytaj obecny CLAUDE.md
2. Przeanalizuj ostatnie zmiany i konwersacje
3. Zaproponuj konkretne zmiany (dodaj/usuń/zmień)
4. Poczekaj na akceptację przed nadpisaniem
