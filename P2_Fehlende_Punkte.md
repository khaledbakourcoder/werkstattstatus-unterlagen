# P2-Check: Fehlende Punkte im Deck „WerkstattStatus P2“

**Stand:** 13.10.2026 · **Präsentation:** P2 am 14.10.2026 · **Geprüft gegen:** P2-Checkliste, allgemeine Checkliste, P1-Deck, Interviews (Nehrkorn Volvo, Kundeninterviews 1–3), Projektstand GitHub

Loco-Soft-Befund wurde auf Wunsch zurückgestellt und ist nicht enthalten.

---

## Priorität 1: Pflichtpunkte der Checkliste (sonst droht „nicht bestanden“)

### 1. Projekt-Tracking zeigen
**Anforderung (6.1):** Board/Tickets, Commit-Aktivität, Fortschrittsindikatoren.

- [ ] Screenshot des GitHub-Project-Boards (Backlog / In Progress / Review / Done)
- [ ] Fortschrittsanzeige, z. B. „X von 32 Tickets erledigt“ (Stand 08.10.: 5 geschlossen, 13 offene P2-Aufgaben, 14 User Stories)
- [ ] Commit-Aktivität (GitHub: Insights → Contributors/Commits), möglichst auf mehrere Personen verteilt
- [ ] Optional: Burndown (braucht gepflegte Story Points, die sind noch leer)

### 2. Geplant vs. Erreicht
- [ ] Gegenüberstellung P1-Plan ↔ Ergebnis (Phase 1 Problemvalidierung, Phase 2 Kundensicht)
- [ ] Zielzahl korrigieren: P1 nannte 2–3 Werkstätten und **5–10 Kunden**, Folie 5 schreibt „Ziel aus P1: 5 Rückmeldungen“. Erreicht: 2 Werkstätten, 3 Kunden
- [ ] Abweichungen vom P1-Plan benennen (siehe Abschnitt „Feedback-Wirkung“)

### 3. Risiken und Blocker
- [ ] Eigene Folie mit je einer Gegenmaßnahme:

| Risiko | Gegenmaßnahme (Vorschlag) |
|---|---|
| Kleine Stichprobe: 3 Kunden, Kunde 1 ist Teammitglied | bis P4 weitere unabhängige Kunden befragen |
| Datenschutz bei Kundendaten und Fotos (Kunde 3, Nehrkorn) | Rollenkonzept, Row Level Security, private Storage-Buckets |
| Parisa trägt zwei Rollen (Requirements + Management) | Aufgaben im Board verteilen, Review durch andere |
| Zeit: Prototyp für P3 am 28.10. | MVP strikt begrenzen, Backlog-Reihenfolge einhalten |

### 4. Offene Fragen und Entscheidungsbedarf
- [ ] Benachrichtigung: nur E-Mail oder mehr? (Folie 10: „als mögliche Erweiterung prüfen“)
- [ ] Kategorisierung der Tickets (Milestones = Sprints, Epics, Labels) im Team entscheiden
- [ ] Protokoll Norden Auto & Service ablegen bzw. Inhalt konkret benennen
- [ ] Weitere unabhängige Kundenbefragung planen

### 5. Anforderungen detailliert und mit Pre-Traceability
**Anforderung (6.3):** testbar, mehr als 10–12 abstrakte Stories; Rationale und Stakeholder je Anforderung.

Aktuell gezeigt: nur US-02 → REQ-03 (Folien 8 und 9).

- [ ] **REQ-Liste** erstellen und zeigen (in den Unterlagen existieren nur US-01 bis US-14; REQ-03/REQ-04 kommen nur auf den Folien vor)
- [ ] Übersichtstabelle US ↔ REQ ↔ Stakeholder ↔ Quelle ↔ Rationale ↔ Priorität (alle 14 oder alle 12 MVP-Stories)
- [ ] Akzeptanzkriterien für mehr als eine Story zeigen (Issues enthalten sie bereits)

Entwurf der Tabelle (REQ-Nummern offen):

| US | REQ | Stakeholder | Quelle | Rationale |
|---|---|---|---|---|
| US-02 Status per Klick | REQ-03 | Mechaniker | Nehrkorn, Abschn. 7 | wenig Schreibaufwand |
| US-03 Abholbenachrichtigung | ? | Kunde | Nehrkorn Abschn. 7, Kunde 1, 2, 3 | 4 von 4 Quellen nennen sie |
| US-05 Digitale Freigabe | ? | Kunde, Serviceberater | Nehrkorn Abschn. 5, 8, Kunde 3 | Kunde telefonisch nicht erreichbar |
| US-07 Vorschäden fotografieren | ? | Serviceberater | Nehrkorn Abschn. 9 | Streit über Vorschäden vermeiden |
| … | | | | |

---

## Priorität 2: Inhaltliche Lücken (Abgleich mit P1 und Interviews)

### Hypothesen (Folie 3)
- [ ] Begründung je Status ergänzen („bestätigt“ / „teilweise“), z. B.:
  - H1: ca. 20 % der Kundenkontakte sind Statusanfragen (Nehrkorn)
  - H2: 3 von 3 Kunden wollen den Status online sehen
  - H3: Nehrkorn „hilfreich, solange kein zusätzlicher Aufwand“; Kunde 1 hatte noch nie Zusatzkosten → Einschränkung nennen
  - H5: belegt ist die Doppelarbeit zwischen Gewerken (Elektriker/Mechaniker), mehr nicht
- [ ] Prüfen, ob H3 wirklich „bestätigt“ heißen darf

### Feedback-Wirkung (Folie 10) erweitern
Aktuell 4 Paare. Ergänzen:
- [ ] **US-03 von „später“ ins MVP hochgestuft** (in P1 „Benachrichtigungen“ unter „Später möglich“). Stärkstes Beispiel für Feedback-Wirkung
- [ ] **Website statt App → PWA** (Kunde 1 und 3)
- [ ] **Kunde ohne Zugriff auf internes System → eigene Kundenansicht** (Nehrkorn Abschn. 2)
- [ ] **Datenschutz → Rollen/Rechte, Row Level Security** (Kunde 3)
- [ ] **Vorschäden fotografieren → US-07** (Nehrkorn Abschn. 9)
- [ ] **Doppelarbeit zwischen Gewerken → Arbeitsschritte mit Mitarbeiter-Zuordnung (US-09)** (Nehrkorn Abschn. 12)

### Befunde (Folie 6) ergänzen
- [ ] Website statt App bevorzugt
- [ ] Datenschutz wichtig
- [ ] Interne Doppelarbeit / Abstimmung zwischen Mitarbeitern
- [ ] Vorschäden bei Annahme dokumentieren
- [ ] Hinweis zur Aussagekraft: Kunde 1 ist ein Teammitglied

### Norden Auto & Service
- [ ] Protokoll liegt in den Unterlagen nicht vor. Ablegen oder konkreten Beitrag auf Folie 5 benennen („Inhalt dokumentiert“ reicht bei Nachfragen nicht)

---

## Priorität 3: Fehler im bestehenden Deck

| Folie | Fehler | Korrektur |
|---|---|---|
| 5 | Kundendatum 12.10.2026 | Protokolle nennen **10.10.2026** |
| 5 | „Ziel aus P1: 5 Rückmeldungen“ | P1 nannte 5–10 Kunden; angleichen |
| 7 | Gruppierung „Anmeldung & Berechtigungen“ enthält US-12, 13, 14 | Nummerierung mit GitHub abgleichen (dort: US-10 Rollen, US-11 Login, US-12 Auftrag anlegen, US-13 Kunden/Fahrzeuge, US-14 Mangel kennzeichnen) |
| 8 | „Beispiel US-02: Statusänderung“ mehrfach übereinander | Dubletten entfernen |
| 10 | „Automatische Abholbenachrichtigung (US-03)“ doppelt | Ein Eintrag löschen |
| 11 | Titel „Vom Feedback zur Konzeptanpassung“ über der Systemarchitektur | Umbenennen in „Skizze der Systemstruktur“ |
| 12 | „Sechs Hypothesen überprüft“, „MVP priorisiert“ | zeigt kein Geplant vs. Erreicht; durch Gegenüberstellung ersetzen |

---

## Sonstiges
- [ ] Sprecherverteilung festlegen, alle vier Teammitglieder einbinden (6.1)
- [ ] Quellenfolie (P1 hatte eine) und KI-Hinweis ergänzen, falls weiter genutzt
- [ ] Commits früh auf mehrere Personen verteilen (wird ab P4 bewertet)

---

## Empfohlene Reihenfolge
1. Tracking-Folie (Board, Fortschritt, Commits)
2. Risiken- und Entscheidungsfolie
3. Anforderungstabelle mit REQ-Liste
4. Folie 10 und 6 erweitern
5. Fehler korrigieren
