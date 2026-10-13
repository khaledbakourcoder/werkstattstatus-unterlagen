# WerkstattStatus – Git-Workflow & Branch-Konzept

WerkstattStatus nutzt ein einfaches, aber strukturiertes Branch-Modell für parallele Entwicklung und stabile Releases.

---

## Das Branch-Konzept

### Zwei Kernzweige

**`main`** – Stabile, präsentierbare Stände. Nur für Releases und Abgaben.

**`develop`** – Gemeinsamer Arbeitsstand. Hier landen alle fertigen Features. Dient als Quelle für neue Feature-Branches.

### Feature-Branches

Jedes Ticket bekommt einen eigenen Branch. Das ermöglicht:
- Parallele Arbeit ohne Konflikte
- Klare Feature-Isolation
- Einfaches Reviewen & Merging

**Namenskonvention:** `<typ>/<ticket-nr>-<beschreibung>`
- Typen: `feat`, `fix`, `docs`, `test`, `chore`
- Beispiel: `feat/18-kunde-statusanzeige`

---

## Workflow-Überblick

Ein Ticket durchläuft diese Phasen:

1. **Branch erstellen** aus `develop` mit Ticketnummer
2. **Entwickeln** – Code schreiben, committen, pushen
3. **Pull Request** auf `develop` öffnen (nicht direkt pushen)
4. **Review & Testing** – CI läuft automatisch
5. **Merge** – Squash-Merge in `develop`, Branch weg
6. **Später:** Wenn fertig → `develop` → `main` (vor Präsentation)

---

## Technische Details

### Commits
Format: `<typ>: <Beschreibung> (#<Ticketnummer>)`

Diese Konvention (Conventional Commits) macht die Historie lesbar:
```
feat: Statusanzeige hinzufügen (#18)
fix: Farbe korrigieren (#33)
test: Edge-Cases (#32)
```

### Keine direkten Pushes nach main/develop
Pull Requests sind der Standard – nicht directes Pushen. Das ermöglicht Code Review, CI-Validierung und automatisches Ticket-Closing.

### Secrets
`.env.local`, `.env.production`, API-Keys gehören nicht ins Git. Das `.gitignore` schützt diese Dateien.

### Testing
CI läuft automatisch bei PR-Erstellung:
- Lint
- Type-Checking
- Tests
- Build

Ein Merge ist erst möglich, wenn die CI grün ist.

---

## Vor einer Präsentation

Alle Tickets sind in `develop` fertig und getestet.

1. PR öffnen: `develop` → `main`
2. Nach Merge: Tag setzen (z. B. `git tag p2`)

Das zeigt später, welcher Codestand präsentiert wurde.

---

## Zusammenfassung

| Aspekt | Entscheidung |
|---|---|
| Feature-Branches | Ja – ein Ticket, ein Branch |
| Direct Pushes | Nein – nur Pull Requests |
| Merge-Strategie | Squash-Merge (saubere Historia) |
| Commit-Format | Conventional Commits mit Ticket-Nummer |
| Secrets-Schutz | `.env*` ignorieren |
| CI vor Merge | Ja – muss grün sein |

---

## Hinweis

Für KI-Agenten (Claude, OpenCode, Hermes) gibt es eine ausführliche Skill-Datei: **`agenten/github.agent.md`**. Diese regelt, wie Agenten dieses Workflow-Konzept technisch umsetzen müssen.
