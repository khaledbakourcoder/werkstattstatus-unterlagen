---
description: "Nutze wenn du den WerkstattStatus Git-Workflow implementierst. Erzwingt Branch-Naming, PR-basierte Merges, Commit-Format, Secrets-Schutz und CI-Validierung."
tags: [git, github, workflow, branching, ci/cd, sicherheit, agenten]
---

# WerkstattStatus GitHub Workflow für Agenten

Vollständige technische Spezifikation für KI-Agenten bei der Implementierung des WerkstattStatus Git-Workflows. Regelt Branch-Operationen, Commits, PRs, Testing und Sicherheit.

---

## Lektionen

### Lektion 1: Branch-Naming und Struktur
**Wann:** Neuer Branch für ein Ticket oder Feature wird erstellt  
**Regel:** Branch-Namen folgen dem Format `<typ>/<ticket-nr>-<kurzbeschreibung>`. Der Typ wird aus einer fixen Liste gewählt: `feat`, `fix`, `docs`, `test`, `chore`. Alle Namen klein geschrieben, mit Bindestrichen statt Leerzeichen.  
**Warum:** Eindeutige, maschinell parsbare Branch-Namen ermöglichen automatische Tools, Linking zu Tickets, und schnelle Orientierung für Entwickler. Das Schema ist in der gesamten GitHub-Historia konsistent.

Gültige Beispiele:
- `feat/18-kunde-statusanzeige`
- `fix/33-farbe-bei-abholbereit`
- `test/32-randfaelle-statuswechsel`
- `docs/16-readme-update`
- `chore/15-ci-pipeline-setup`

Ungültige Beispiele:
- `feature/18-statusanzeige` (falscher Typ)
- `feat/statusanzeige` (keine Ticket-Nr)
- `feat/18_kunde_statusanzeige` (Underscore statt Bindestrich)

---

### Lektion 2: Feature-Branch-Ursprung und Basis
**Wann:** Neuer Branch wird zum ersten Mal erstellt  
**Regel:** Feature-Branches entstehen IMMER aus `origin/develop`, nicht aus `main`. Bei der Erstellung wird `--no-track` verwendet, um zu vermeiden, dass der Branch automatisch `origin/develop` tracked.  
**Warum:** `develop` ist der Integrationspunkt. Alle Features bauen auf demselben Arbeitsstand auf. `--no-track` ermöglicht asynchrones Arbeiten ohne automatische Upstream-Konflikte.

Korrekt:
```bash
git fetch
git switch -c feat/18-statusanzeige --no-track origin/develop
```

Nicht korrekt:
```bash
git switch -c feat/18-statusanzeige origin/main  # ← main ist für Release, nicht für Features
git switch feat/18-statusanzeige  # ← --no-track fehlt
```

---

### Lektion 3: Conventional Commits mit Ticketnummer
**Wann:** Commit-Nachricht wird verfasst  
**Regel:** Commits folgen dem Format `<typ>: <Beschreibung> (#<Ticketnummer>)`. Der Typ ist identisch mit dem Branch-Typ. Die Beschreibung ist kurz, im Präsens, aktiv. Die Ticketnummer in Klammern ist ERFORDERLICH.  
**Warum:** Conventional Commits sind maschinenlesbar. Tools können automatisch Changelogs generieren, Release-Notes aufbauen, und Commits zu Tickets verlinken. Die Ticketnummer ist kritisch für "Closes #18" in PR-Beschreibungen.

Gültig:
```
feat: Statusanzeige hinzufügen (#18)
fix: Farbe korrigieren (#33)
test: Randfälle abdecken (#32)
docs: API-Dokumentation aktualisieren (#16)
chore: Abhängigkeiten aktualisieren (#15)
```

Ungültig:
```
feat: Statusanzeige  # ← Keine Ticketnummer
#18 Statusanzeige  # ← Falsches Format
feat(kunde): Statusanzeige (#18)  # ← Scope nicht nötig (Branch-Typ reicht)
```

---

### Lektion 4: Pull Requests statt direkter Pushes zu main/develop
**Wann:** Feature ist fertig und soll in develop integriert werden  
**Regel:** Feature-Branches werden NIEMALS direkt nach `main` oder `develop` gepusht. Stattdessen wird ein Pull Request mit `gh pr create --base develop` geöffnet. Der PR-Body muss "Closes #<Ticketnummer>" enthalten, damit GitHub das Ticket automatisch schließt. Nur nach erfolgreicher CI und mindestens einem Review wird gemergt.  
**Warum:** PRs sind das Code-Review-Gate. Sie erzwingen Qualität, machen Änderungen sichtbar und dokumentieren Entscheidungen. CI-Validierung vor Merge verhindert kaputten Code auf dem Mainline.

Korrekt:
```bash
git fetch
git merge origin/develop  # Lokal synchronisieren
gh pr create --base develop   --title "Statusanzeige (#18)"   --body "Closes #18

Implementiert die Anzeige des aktuellen Werkstatt-Status für Kunden."
```

Nie erlaubt:
```bash
git push origin HEAD:develop  # ← Direkter Push, kein PR
git push origin HEAD:main  # ← Direkt zu main, sehr verboten
git push --force  # ← Force-Push zerstört Historie
```

---

### Lektion 5: Tägliches Abgleichen mit develop (bei längeren Branches)
**Wann:** Feature wird länger als 2–3 Tage bearbeitet  
**Regel:** Täglich (oder bei großen Changes in develop) `git fetch` + `git merge origin/develop` durchführen. Das hält den Feature-Branch aktuell und verhindert Merge-Konflikte am Ende. Falls Konflikte entstehen, müssen sie sofort gelöst werden.  
**Warum:** Kleine, häufige Merges sind psychologisch einfach. Große, seltene Merges = Konflikte, Stress, Datenverlust-Risiko. Tägliches Abgleichen reduziert Kontextwechsel und hält Branches kurzlebig.

Workflow:
```bash
git fetch
git merge origin/develop
# Falls Konflikte:
#   - Datei öffnen
#   - Konflikte manuell auflösen
#   - git add <datei>
#   - git commit (kein -m, Auto-Merge-Message)
git push
```

---

### Lektion 6: Konflikte nicht automatisch auflösen (Agent-Regel)
**Wann:** `git merge origin/develop` zeigt Konflikte  
**Regel:** Agenten dürfen Merge-Konflikte NICHT automatisch auflösen. Stattdessen: `git merge --abort` und Benachrichtigung an den Entwickler mit Details zu den konfliktären Dateien.  
**Warum:** Merge-Konflikte haben oft nicht-offensichtliche Semantik. Automatische Auflösung kann Silent Bugs, Logik-Fehler und Daten-Verlust verursachen. Nur der Entwickler, der beide Seiten kennt, sollte entscheiden.

Korrekt (Agent):
```bash
git fetch
git merge origin/develop
# Konflikte detected
git merge --abort
# Log: "Merge-Konflikte erkannt. Entwickler muss auflösen:
#       - src/components/Status.tsx (Zeile 45-67)
#       - src/utils/status.ts (Zeile 12-18)"
```

Nie:
```bash
git merge origin/develop
# Konflikte → Datei öffnen → Auto "reparieren" → commit & push ❌
```

---

### Lektion 7: CI muss grün sein vor Merge
**Wann:** PR ist fertig und soll gemergt werden  
**Regel:** Die GitHub Actions CI (Lint, Typecheck, Tests, Build) muss für den PR grün sein. Kein Merge ist erlaubt, wenn:
- Tests schlagen fehl
- Lint-Fehler vorhanden sind
- TypeScript-Errors nicht gelöst sind
- Build schlägt fehl

Agenten dürfen keinen Code pushen, der diese Checks nicht lokal bestanden hat.

**Warum:** Die CI ist das finale Quality-Gate. Sie stellt sicher, dass der Code buildet, keine Linting-Fehler enthält, und alle Tests bestanden sind. Code, der die CI nicht bestanden hat, muss nicht gemergt werden.

Pre-Push-Check:
```bash
npm run lint
npm run typecheck
npm run test
npm run build
# Alle grün? → git push
# Eine rot? → Code fixen, Loop zurück
```

---

### Lektion 8: Secrets und .env-Dateien niemals committen
**Wann:** Kurz bevor `git add .` oder `git push` ausgeführt wird  
**Regel:** Vor JEDEM `git add .` muss `git status` überprüft werden. `.env`, `.env.local`, `.env.production`, `.env.*.local`, sowie alle Dateien mit Secrets (API-Keys, Passwörter, private URLs, JWTs) dürfen NIEMALS in Git landen. Das `.gitignore` muss diese Dateien enthalten.  
**Warum:** Secrets in Git sind für immer. Sie können technisch nicht entfernt werden, ohne die komplette Historia zu rewritten. Das ist ein Sicherheitsleck für das ganze Projekt. Wenn eine Datei versehentlich committed wurde, muss sie mit `git reset HEAD~1` rückgängig gemacht und `.gitignore` aktualisiert werden.

Sichere `.gitignore`:
```
.env
.env.local
.env.*.local
.env.production
*.key
*.pem
node_modules/
.DS_Store
```

Pre-Commit-Check:
```bash
git status
# Zeigt .env.local? → STOP, nicht committen!
# Zeigt *.key? → STOP!
# Saubere Dateien? → git add . OK
```

---

### Lektion 9: Squash-Merge für saubere Historia
**Wann:** PR wird in develop gemergt  
**Regel:** PRs werden mit Squash-Merge gemergt (eine Umwandlung aller Commits in einen einzelnen Commit). Das ist eine GitHub-Einstellung auf dem Repo. Nach dem Merge wird der Branch automatisch gelöscht.  
**Warum:** Squash-Merge hält die Historia auf `develop` sauber und lesbar. Jedes Feature zeigt sich als ein großer Commit, nicht als 10 WIP-Commits. Das erleichtert `git log`-Navigation und Revert-Operationen.

GitHub-Einstellung:
```
Repo Settings → Pull requests → 
  [✓] Allow squash merging
  [ ] Allow merge commits
  [ ] Allow rebase merging
  [✓] Auto-delete head branches
```

---

### Lektion 10: Force-Push ist verboten
**Wann:** Versuchung entsteht, `git push --force` zu verwenden  
**Regel:** Force-Push (`git push --force`, `git push -f`) ist auf `main`, `develop` und allen kollaborativen Branches verboten. Falls "rejected (fetch first)", ist das normal → `git fetch`, `git merge origin/develop`, `git push` (normaler Push).  
**Warum:** Force-Push überschreibt die Remote-Historie. Das zerstört parallele Arbeit, kann Commits anderer Entwickler löschen, und ist in Teams ein großes Risiko. Ein normaler `git merge` ist immer die richtige Antwort.

Richtig:
```bash
git push
# rejected (fetch first)
git fetch
git merge origin/develop
git push  # ← Normal!
```

Falsch:
```bash
git push --force  # ❌ NIEMALS
git push -f  # ❌ NIEMALS
```

---

### Lektion 11: Ein Ticket = Ein Branch
**Wann:** Arbeit wird über mehrere zusammenhängende Issues geplant  
**Regel:** Jedes Ticket bekommt exakt einen Branch. Falls mehrere Tickets zusammenhängen oder aufeinander bauen, werden separate Branches und separate PRs erstellt. Ein Branch adressiert EINE Issue-Nummer.  
**Warum:** Ermöglicht unabhängiges Reviewen und Merging. Falls ein Feature reverted werden muss, sind andere nicht betroffen. Macht die Git-Historia granular und nachverfolgbar.

Richtig:
```
feat/18-kunde-statusanzeige  → Closes #18
feat/19-werkstatt-status-settings  → Closes #19
```

Falsch:
```
feat/18-19-statusanzeige-und-settings  # ← Zwei Tickets!
feat/18-und-alles-andere  # ← Zu breit
```

---

### Lektion 12: PR-Body mit "Closes #Ticketnummer"
**Wann:** Pull Request wird geöffnet  
**Regel:** Der PR-Body MUSS die Phrase "Closes #<Ticketnummer>" enthalten. Das ist eine GitHub-Konvention: Wenn der PR gemergt wird, schließt GitHub das Ticket automatisch. Der Standard-Branch muss auf `develop` gesetzt sein, damit das funktioniert.  
**Warum:** Automatisches Ticket-Closing hält das Project-Board synchron mit der Realität. Keine manuellen Steps nötig.

Gültiger PR-Body:
```
Closes #18

## Was wurde implementiert
- Statusanzeige Komponente
- Styling angepasst
- Tests hinzugefügt

## Testing-Hinweise
- Manuell in Chrome und Firefox getestet
- Unit-Tests: 5 neue Tests, alle grün
```

---

### Lektion 13: Täglich pushen (auch unfertiges)
**Wann:** Tagesende oder logischer Checkpoint  
**Regel:** Tägliches Pushen ist normal, auch wenn das Feature nicht fertig ist. Die Regel "Unfertiges kommt nicht nach `develop`" bedeutet: unfertiger Code ist OK im Feature-Branch, aber nicht nach `develop` ohne PR & Review.  
**Warum:** Tägliches Pushen ist eine Backup-Strategie. Es sichert Fortschritt und ermöglicht Zusammenarbeit auf derselben Branch (z. B. Pair-Programming).

Korrekt:
```bash
# Ende des Tages
git commit -m "feat: WIP - Statusanzeige Layout (#18)"
git push
# ← Feature-Branch gepusht, aber nicht gemergt. Andere können pullen.
```

Nie:
```bash
# Unfertiges nach develop pushen
git push origin HEAD:develop  # ❌
```

---

### Lektion 14: Präsentationsstände mit Tags
**Wann:** Präsentation findet statt oder Release wird vorbereitet  
**Regel:** Bevor eine Präsentation stattfindet, wird `develop` in `main` gemergt (PR). Nach dem Merge wird ein Git-Tag gesetzt: `git tag p1`, `git tag p2`, etc. Das Tag markiert exakt welcher Codestand präsentiert wurde.  
**Warum:** Tags ermöglichen Zeitreisen. Später kannst du `git checkout p2` ausführen und den exakten Code reproducieren, der in Präsentation 2 gezeigt wurde. Hilft bei Bug-Reports ("Das war in p2 broken") und historischem Context.

```bash
git tag p2
git push origin p2
```

---

### Lektion 15: Develop ist Standard-Branch
**Wann:** GitHub Repository-Einstellungen werden überprüft  
**Regel:** Der Standard-Branch auf GitHub muss `develop` sein (nicht `main`). Das stellt sicher, dass neue PRs automatisch auf `develop` zielen und "Closes #18" funktioniert.  
**Warum:** Verhindert versehentliche PRs zu `main`. Zentralisiert den Workflow auf `develop` als Integrationspunkt.

GitHub-Einstellung:
```
Repo Settings → General → Default branch → develop
```

---

## Agent-Workflows

### Workflow A: Neues Feature vom Start bis PR

```bash
# 1. Ticket: #18 "Statusanzeige"
git fetch
git switch -c feat/18-kunde-statusanzeige --no-track origin/develop

# 2. Entwickeln
npm run dev  # ← Editor, Codeänderungen, Tests lokal

# 3. Tests & Linting lokal
npm run lint       # ← Muss grün sein
npm run typecheck  # ← Muss grün sein
npm run test       # ← Muss grün sein
npm run build      # ← Muss erfolgreich sein

# 4. Commit
git add .
git status  # ← KEIN .env.local, KEINE Secrets!
git commit -m "feat: Statusanzeige hinzufügen (#18)"

# 5. Mit develop abgleichen
git fetch
git merge origin/develop
# Falls Konflikte: (Agent) merge --abort + Warnung

# 6. Push
git push -u origin HEAD

# 7. PR öffnen (NICHT pushen!)
gh pr create --base develop   --title "Statusanzeige (#18)"   --body "Closes #18

Implementiert die Live-Statusanzeige für Kunden mit Farbcoding."

# 8. CI läuft, Review kommt, Merge erfolgt (nicht durch Agent!)
```

### Workflow B: Änderungen während PR-Review

```bash
# Feedback gekommen: "Farbe ist falsch"

# 1. Änderungen lokal machen
# (Editor, Code-Änderungen)

# 2. Tests & Lint
npm run test
npm run lint

# 3. Commit zu bestehender Branch
git add .
git commit -m "fix: Farbe korrigieren (#18)"

# 4. Push
git push  # ← PR updated sich automatisch

# 5. Warte auf Re-Review
```

### Workflow C: Tägliches Abgleichen (lange Feature)

```bash
# Feature dauert länger als 2-3 Tage
# Täglich:

git fetch
git merge origin/develop
# Falls Konflikte:
#   git merge --abort + Warnung
# Kein Konflikt:
git push
```

---

## Sicherheits-Checklist für Agenten

Vor JEDEM Push oder PR:

```
[ ] git status geprüft → KEINE .env*, KEINE *.key, KEINE Secrets
[ ] npm run lint → grün
[ ] npm run typecheck → grün
[ ] npm run test → grün
[ ] npm run build → erfolgreich
[ ] Commit-Format: "<typ>: ... (#<Nr>)" ✓
[ ] Branch-Name: "<typ>/<Nr>-..." ✓
[ ] Bin ich auf einem Feature-Branch? (nicht main/develop)
[ ] fetch + merge origin/develop → konfliktfrei?
```

Falls EINE Frage nicht bestanden ist:
- STOP, nicht pushen
- Fehler beheben
- Loop zurück

---

## Fehlerbehebung

| Fehler | Lösung | Agent-Aktion |
|---|---|---|
| "rejected (fetch first)" | `git fetch`, `git merge origin/develop`, `git push` | Normal, nicht --force |
| Merge-Konflikte | Manuell auflösen (Entwickler) | STOP + Warnung, merge --abort |
| Tests schlagen fehl | Code fixen, Tests lokal rerun | STOP, nicht pushen |
| `.env.local` in git status | Datei in `.gitignore` add, `git reset HEAD~1` | STOP, nicht committen |
| Branch-Name falsch | `git branch -m <new-name>` | Neu anfangen mit richtigem Namen |
| Zu `main` pushen versucht | PR zu `develop` statt `main` | STOP, nur develop |
| Force-Push-Versuchung | Normal `git push` + merge | STOP, nie --force |

---

## Werkzeuge

- `git` – Versionskontrolle
- `gh` – GitHub CLI (`gh pr create`, `gh issue view`)
- `npm run lint` – Syntax/Style-Check
- `npm run typecheck` – TypeScript-Validierung
- `npm run test` – Unit & Integration Tests
- `npm run build` – Production Build

---

## Zusammenfassung: Was Agenten tun müssen

1. ✅ Branch-Namen: `<typ>/<nr>-<beschreibung>`
2. ✅ Commits: `<typ>: <beschreibung> (#<nr>)`
3. ✅ PR statt Push: `gh pr create --base develop`
4. ✅ PR-Body: "Closes #18"
5. ✅ Tests vor Push: Alle grün
6. ✅ Keine Secrets: `.env*` prüfen
7. ✅ Konflikte: merge --abort + Warnung
8. ✅ Tägliches Abgleichen: `git merge origin/develop`

---

## Zusammenfassung: Was Agenten NICHT tun dürfen

1. ❌ Direkt zu `main` oder `develop` pushen
2. ❌ Force-Push (`--force`, `-f`)
3. ❌ Secrets committen
4. ❌ Konflikte selbst auflösen
5. ❌ Tests/Lint überspringen
6. ❌ Mehrere Tickets in einem Branch
7. ❌ Code mergen (nur PR öffnen)
8. ❌ Zu `main` arbeiten
