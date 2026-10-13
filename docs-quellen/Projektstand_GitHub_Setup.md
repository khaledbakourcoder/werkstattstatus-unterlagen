# WerkstattStatus – Projektstand GitHub-Setup und Tracking

**Stand:** 08.10.2026 · **Erstellt von:** Khaled (mit Claude) · **Nächster Termin:** P2 am 14.10.2026

---

## 1. Was bereits eingerichtet ist

### GitHub-Zugang (Khaled)
- Account: `khaledbakourcoder`
- SSH-Key (ed25519) lokal erzeugt unter `C:\Users\khale\.ssh\id_ed25519` und per `gh auth login` bei GitHub hochgeladen (Titel „GitHub CLI“).
- GitHub CLI angemeldet, Git-Protokoll SSH, Projektrechte über `gh auth refresh -s project`.

### Repository
- Name: `khaledbakourcoder/werkstattstatus`
- Collaborators mit Schreibrechten (`write`) eingeladen: Sami (`Sami1247`), Mohammad, Parisa.
- Einladungen müssen angenommen werden: https://github.com/khaledbakourcoder/werkstattstatus/invitations
- *Zu prüfen:* öffentlich oder privat angelegt.

### GitHub Project (Board)
- Owner: `khaledbakourcoder`, Projektnummer: *(bitte eintragen)*
- Alle drei Teammitglieder mit Rolle **Write** eingeladen.
- Hinweis: Project-Zugriff und Repo-Zugriff sind getrennt; beide sind vergeben.

### Setup-Skript `setup_board.sh` (erfolgreich ausgeführt)
**Projektfelder:** Aktivität (Requirements, Architektur, Implementierung, QA, Management) · Priorität (MVP, Später) · Story Points (Zahl, noch leer)

**Labels (12):**

| Gruppe | Labels |
|---|---|
| Typ | `user-story`, `aufgabe`, `präsentation` |
| Priorität | `mvp`, `später` |
| Bereich | `bereich:status`, `bereich:freigabe`, `bereich:historie`, `bereich:doku`, `bereich:rollen`, `bereich:intern` |
| Herkunft | `quelle:interview` |

**Issues (32):**
- 5 erledigt (geschlossen): P1-Präsentation, Interviewleitfaden, Interview Nehrkorn Volvo, Interviewprotokoll, Projekt-Board einrichten
- 13 offene Aufgaben für P2: Anforderungen dokumentieren, Hypothesen H01–H06 abgleichen, Feedback-Dokumentation, Interview N.A.S Wallsbüll, Kundenumfrage, Systemstruktur skizzieren, Entscheidung Loco-Soft, Repo-Grundstruktur Next.js/Supabase, Coding-Standards, CI-Pipeline, Teststrategie, P2 vorbereiten
- 14 User Stories (Entwurf, von Parisa zu prüfen), jeweils mit Akzeptanzkriterien, Rationale und Interview-Abschnitt:

| ID | User Story | Priorität |
|---|---|---|
| US-01 | Kunde sieht aktuellen Reparaturstatus | MVP |
| US-02 | Mitarbeiter aktualisiert Status mit einem Klick | MVP |
| US-03 | Automatische Benachrichtigung „abholbereit“ (in P1 noch „später“, durch Interview hochgestuft) | MVP |
| US-04 | Serviceberater stellt Zusatzarbeit mit Kosten zur Freigabe ein | MVP |
| US-05 | Kunde gibt Zusatzarbeit digital frei oder lehnt ab | MVP |
| US-06 | Kostenlimit für Zusatzarbeiten | Später |
| US-07 | Vorschäden bei Annahme fotografieren | MVP |
| US-08 | Reparaturhistorie eines Fahrzeugs | MVP |
| US-09 | Arbeitsschritte abhaken mit Mitarbeiter-Zuordnung | MVP |
| US-10 | Rollen und Rechte | MVP |
| US-11 | Login | MVP |
| US-12 | Reparaturauftrag anlegen | MVP |
| US-13 | Kunden und Fahrzeuge verwalten | MVP |
| US-14 | Sicherheitsrelevanten Mangel kennzeichnen | Später |

---

## 2. Erkenntnisse für P2

- **Technisch gefordert in P2:** nur eine grobe *Skizze der Systemstruktur* (Wochenplan) und der *Stand des Projekt-Trackings* (allgemeine Checkliste: Board, Commit-Aktivität, Fortschritt). Detail-Architektur und Prototyp erst in P3.
- **Vorschlag Systemskizze:** Next.js-PWA mit getrennter Werkstatt- und Kundenansicht → Supabase (Auth, DB, Storage) → Benachrichtigung (E-Mail). Trennung der Sichten begründet durch Interview Abschnitt 2.
- **Offene Frage für P2:** Nehrkorn nutzt seit 01.10. Loco-Soft. Eigenständiges System (kleine Werkstätten ohne Software) oder schlanke Kunden-Statusschicht neben bestehender Software? Doppelte Datenpflege widerspricht „kein zusätzlicher Aufwand“.
- **Feedback-Wirkung zeigen:** US-03 Benachrichtigungen von „später“ ins MVP hochgestuft.

---

## 3. Offene Entscheidungen (im Team klären)

### Kategorisierung der Tickets
Problem: Präsentation, Systembereich und MVP beantworten verschiedene Fragen; eine Story betrifft oft mehrere Systemteile.

| Ansatz | Kern | Vorteil | Nachteil |
|---|---|---|---|
| A: Dimensionen | Milestone (bis wann), Priorität, Aktivität, Typ, Schicht getrennt | Klare Filter, Statistik pro Rolle | Große Stories bekommen mehrere Schicht-Labels |
| B: Hierarchie | Epic → User Story → Teilaufgabe (Sub-Issues) | Zusammenhang sichtbar, beste Traceability | Viele Tickets, mehr Pflegeaufwand |
| C: Vertical Slices | Nur nach Funktion, Story wird komplett umgesetzt | Wenig Aufwand, nah an Scrum | Keine technische Sicht, Tests weniger sichtbar |

**Empfehlung (B + A, pragmatisch):**
1. Milestones = Sprints = Präsentationen (Sprint 1 endet mit P2, Sprint 2 mit P3 …) – ersetzt eine eigene „P-Kategorie“.
2. Epics für die sechs Interview-Bereiche (ersetzen die `bereich:`-Labels).
3. Teilaufgaben nur für den aktuellen Sprint anlegen.
4. Technische Labels nur auf Teilaufgaben; braucht eine Teilaufgabe mehr als ein Schicht-Label, ist sie zu groß.
5. Eine Story wird gemeinsam bis zur vorführbaren Funktion fertig gemacht.
6. Entscheidung mit Begründung dokumentieren (Management-Bewertung).

### Vorgeschlagene technische Labels (noch nicht angelegt)
`frontend`, `backend`, `datenbank`, `test`, `bug` (Pflicht für Defekt-Tracking), `infrastruktur`, `dokumentation`

### Vorgeschlagene Backlog-Reihenfolge (aus Interview Abschnitt 11)
1. Grundlage: US-11, US-10, US-13, US-12
2. Weniger Statusanfragen: US-02, US-01, US-03
3. Arbeitsschritte abhaken: US-09
4. Historie: US-08
5. Freigaben: US-04, US-05
6. Fotos: US-07
7. Später: US-06, US-14

---

## 4. Noch zu erledigen

- [ ] Einladungen von allen drei angenommen? (Repo: Settings → Collaborators)
- [ ] Projektnummer und Sichtbarkeit des Repos oben eintragen
- [ ] Optionen „Backlog“ und „Review“ im Status-Feld ergänzen (falls nicht geschehen)
- [ ] Iteration-Feld „Sprint“ (2 Wochen) manuell im Project anlegen
- [ ] Milestones P2–P7 mit Datum anlegen
- [ ] Kategorisierung im Team entscheiden, danach Labels/Epics anpassen
- [ ] Backlog per Drag & Drop ordnen
- [ ] Story Points im Sprint Planning schätzen
- [ ] User Stories mit Parisa abstimmen
- [ ] Später: Dozent (Kai Petersen) mit Read-Rechten in Repo und Project einladen

---

## 5. Arbeitsablauf Ticket → Code (vereinbart als Vorschlag)

1. Issue zuweisen, Karte auf „In Progress“.
2. Branch aus dem Issue erstellen: `gh issue develop <nr> --checkout`
3. Commits mit Issue-Nummer: `git commit -m "… (#<nr>)"`
4. Pull Request mit `Closes #<nr>`, Review durch QA (Mohammad), CI läuft.
5. Merge → Issue schließt sich, Karte wandert automatisch nach „Done“.

Aufgaben ohne Code (Interviews, Doku) werden manuell geschlossen.
