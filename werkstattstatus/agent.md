# Agent Guidelines – WerkstattStatus

Leitfaden für KI-Agenten (Claude, OpenCode, Hermes) bei der Arbeit im WerkstattStatus-Projekt.

---

## 📋 Grundregeln

### Branch-Workflow
- **Ein Ticket = Ein Branch** mit Schema: `<typ>/<nr>-<beschreibung>`
- Typen: `feat`, `fix`, `docs`, `test`, `chore`
- Beispiel: `feat/18-kunde-statusanzeige`

### Commits
Format: `<typ>: <Beschreibung> (#<Nr>)`
```
feat: Statusanzeige hinzufügen (#18)
fix: Farbe korrigieren (#33)
chore: Dependencies aktualisieren (#15)
```

### Pull Requests
- ✅ **Immer PR öffnen** – kein direkter Push zu `main` oder `develop`
- ✅ **PR-Body:** "Closes #<Nr>" (schließt Ticket automatisch)
- ✅ **Basis:** `develop` (nicht `main`)
- ✅ **Merging:** Squash-Merge nach Review + grüner CI

### Sicherheit
- ❌ **NIEMALS:** Secrets, `.env.local`, API-Keys committen
- ✅ **VOR `git add .`:** `git status` prüfen
- ✅ **`.gitignore` muss enthalten:** `.env*`, `*.key`, `*.pem`

### CI & Testing
- ✅ Lokal testen vor Push: `npm run lint && npm run build`
- ✅ Alle npm scripts müssen grün sein
- ✅ CI muss bestanden sein für Merge

---

## 🗂️ Projektstruktur

```
werkstattstatus/
├── app/                  ← Next.js Projekt (Node.js v22)
│   ├── package.json
│   ├── .nvmrc           ← Node-Version
│   ├── app/             ← Next.js App Router
│   └── ...
├── .github/
│   └── workflows/
│       └── ci.yml       ← GitHub Actions (Lint, Build)
├── docs/
│   └── Git-Workflow.md  ← Detaillierter Git-Workflow
├── agenten/
│   └── github.agent.md  ← Spezifische GitHub-Regeln für Agenten
├── agent.md             ← DIESE DATEI (Zentrale Agenten-Guidelines)
└── README.md            ← Projekt-Übersicht
```

---

## 🚀 Workflow: Von Ticket bis Merge

### 1. Branch erstellen
```bash
git fetch
git switch -c feat/18-statusanzeige --no-track origin/develop
```

### 2. Code schreiben & committen
```bash
git add .
git commit -m "feat: Statusanzeige (#18)"
git push -u origin HEAD
```

### 3. Pull Request öffnen
```bash
gh pr create --base develop \
  --title "Statusanzeige (#18)" \
  --body "Closes #18"
```

### 4. Review + CI
- GitHub Actions läuft automatisch (Lint, Build)
- Mindestens eine Person reviewt (Standard: Mohammad)
- Wenn alles grün → Squash-Merge

### 5. Fertig!
- Ticket schließt sich automatisch (wegen "Closes #18")
- Branch wird gelöscht
- Code ist in `develop`

---

## 📚 Weitere Dokumentation

- **[Git-Workflow](./docs/Git-Workflow.md)** – Detailliertes Branch-Konzept für Menschen
- **[GitHub Agent Skill](./agenten/github.agent.md)** – Spezifische Regeln für KI-Agenten bei GitHub-Operationen

---

## ⚡ Häufige Fehler

| Problem | Lösung |
|---|---|
| "rejected (fetch first)" | `git fetch` → `git merge origin/develop` → `git push` |
| Merge-Konflikte | Nicht selbst lösen! `git merge --abort` und Developer benachrichtigen |
| `.env.local` committed | `git reset HEAD~1`, Datei zu `.gitignore`, neuer Commit |
| Branch-Name falsch | `git branch -m <neuer-name>`, neuer Push |
| Tests lokal bestanden, CI fehlgeschlagen | Dependency-Issue? Lokal `npm ci` statt `npm install` testen |

---

## 🤖 Für KI-Agenten: Was NICHT erlaubt

❌ Direkt zu `main` oder `develop` pushen  
❌ Force-Push (`git push --force`)  
❌ Secrets/API-Keys committen  
❌ Mehrere Tickets in einem Branch  
❌ Merge-Konflikte selbst auflösen  
❌ Tests/Lint überspringen  
❌ Code mergen (nur PR öffnen)  
❌ Zu `main` arbeiten (nur Feature-Branches)  

---

## ❓ Fragen?

Schau zuerst in [Git-Workflow.md](./docs/Git-Workflow.md) oder [github.agent.md](./agenten/github.agent.md) nach.
