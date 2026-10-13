# Software-Projekt WS 2026/27 – Extrahierte Projektdaten

**Projekt:** WerkstattStatus · **Team:** Mohammad, Khaled, Parisa, Sami
**Kurs:** Software-Projekt, Hochschule Flensburg, Kai Petersen (kai.petersen@hs-flensburg.de)

---

## 0. Extraktionsprotokoll

Die drei Quelldateien wurden mit **Microsoft MarkItDown** konvertiert. Technischer Hinweis: Die Dateien tragen die Endung `.pdf`, sind aber ZIP-Archive (pro Seite ein JPEG-Bild plus eine Textebene und eine `manifest.json`). MarkItDown hat sie korrekt als ZIP gelesen.

| Quelldatei | Seiten laut Manifest | Seiten mit Text extrahiert | Status |
|---|---|---|---|
| `WerkstattStatus_Project_3.pdf` | 11 | 11 | vollständig, mit Korrekturen |
| `L01_Projekt_Tips_WS26_27_key.pdf` | 19 | 19 | vollständig, mit Korrekturen |
| `Software_Project_WS_2026_27.pdf` | 12 | 12 | vollständig, Tabellen rekonstruiert |

**Gefundene und korrigierte Extraktionsfehler:**

1. **Folie 8 „Tools & Technologie“ (WerkstattStatus):** Die Textebene enthält eine *veraltete Version* der Folie (PostgreSQL + Prisma, Clockify, draw.io …). Das Folienbild zeigt den aktuellen Stack (Supabase ersetzt PostgreSQL + Prisma). Übernommen wurde der Inhalt **laut Folienbild**.
2. **Folien 6 und 7 (WerkstattStatus):** Leerzeichen fehlten („ieentwickelnwirdas?“, „DigitaleFreigabe/Ablehnung“). Anhand der Bilder korrigiert.
3. **Folie 10 „Das Team“:** Namen und Rollen standen durcheinander. Zuordnung anhand des Bildes wiederhergestellt.
4. **L01 Folie 17:** Zeichenfehler durch Ligaturen („Sta$c“, „Inspec$ons“, „Condi4on“) korrigiert.
5. **Kursbeschreibung:** Bewertungsrubrik-Tabellen waren in Einzelwörter zerfallen, Trennzeichen (`\u0002`) steckten in Wörtern. Tabellen wurden neu aufgebaut.
6. **Hinweis L01:** Die Agenda nennt „Beispiele für unterstützende Anwendungen“ und „Plangetrieben vs. Agil“. Zu diesen Punkten gibt es in der Datei **keine Folien** (Datei endet nach Folie 19 „Versions- und Konfigurationsmanagement“). Das ist kein Extraktionsfehler, der Inhalt fehlt in der Quelle.

Rein visuelle Inhalte (Mockups, Illustrationen, Logos) sind nicht als Text enthalten; relevante Beschriftungen aus den Mockups sind unten ergänzt und als solche markiert.

---

## 1. Projektpräsentation P1 – WerkstattStatus

*Quelle: `WerkstattStatus_Project_3.pdf` (11 Folien)*

### Folie 1 – Titel

**WerkstattStatus** – Digitale Service- und Auftragsplattform für Kfz-Werkstätten.

- **Mehr Transparenz** für Kunden
- **Weniger Abstimmungsaufwand** für Werkstätten

Team: Mohammad • Khaled • Parisa • Sami

*Smartphone-Mockup „Auftragsstatus“:* Annahme → Diagnose → In Bearbeitung → Qualitätsprüfung → Abgeschlossen

### Folie 2 – Welches Problem lösen wir?

Herausforderungen im Werkstattalltag heute:

| Problem | Beschreibung |
|---|---|
| Viele Statusanfragen | Kunden fragen telefonisch nach Reparaturstand und Fertigstellung. |
| Langsame Freigaben | Zusätzliche Reparaturen und Mehrkosten werden telefonisch abgestimmt und verzögern den Auftrag. |
| Verteilte Informationen | Diagnose, Fotos, Kosten, Ersatzteile und Entscheidungen liegen an verschiedenen Stellen. |
| Unterbrechungen im Werkstattalltag | Wiederkehrende Rückfragen unterbrechen Mitarbeitende und kosten wertvolle Zeit. |

### Folie 3 – Unsere Lösung

WerkstattStatus verbindet Werkstatt und Kunden auf einer Plattform.

**Kunde**
- Status online verfolgen
- Freigaben digital erteilen
- Fotos und Dokumente einsehen
- Reparaturhistorie behalten

**Werkstatt**
- Aufträge zentral verwalten
- Mitarbeitende und Aufgaben zuweisen
- Diagnosen, Bilder und Notizen dokumentieren
- Kunden transparent informieren

**Kernprozess (9 Schritte)**

| Nr. | Schritt |
|---|---|
| 01 | Terminanfrage |
| 02 | Fahrzeugannahme |
| 03 | Diagnose |
| 04 | Kostenvoranschlag |
| 05 | Freigabe |
| 06 | Reparatur |
| 07 | Qualitätskontrolle |
| 08 | Abholbereit |
| 09 | Abschluss |

Leitsatz: *Ein gemeinsamer Informationsstand für Werkstatt und Kunde.*

*(Die Textebene enthält zusätzlich das Wort „Anlage“ – ein abgeschnittenes Etikett aus dem Mockup ohne eigene Bedeutung.)*

*Mockup (Desktop):* Navigation Übersicht, Aufträge, Kunden, Fahrzeuge, Mitarbeitende, Einstellungen; Auftragsübersicht mit Statusleiste Annahme → Diagnose → Angebot → Freigabe → Reparatur → Abschluss; Beispielauftrag VW Golf VII (AB-WS 123), Status „Reparatur“; Aktivitäten (Diagnose, Kostenvoranschlag, Freigabe); Bereich „Dokumente & Fotos“.
*Mockup (Mobil):* Status, „Nächster Schritt: Qualitätskontrolle“, Dokumente; Tabs Übersicht, Dokumente, Verlauf.

### Folie 4 – Zielgruppe & Wertversprechen

| Nr. | Zielgruppe | Nutzen |
|---|---|---|
| 01 | Kleine und mittelständische Kfz-Werkstätten | Weniger Telefonaufwand, bessere Übersicht und dokumentierte Abläufe. |
| 02 | Fahrzeugkunden | Status online verfolgen, digitale Entscheidungen treffen und Dokumente zentral abrufen. |

**Wertversprechen:** Weniger Kommunikationsaufwand für Werkstätten. Mehr Transparenz und schnellere Entscheidungen für Kunden.

### Folie 5 – Zentrale Hypothesen

Unsere Annahmen – zur Validierung durch Interviews, Feedback und Tests.

| Nr. | Hypothese | Annahme |
|---|---|---|
| H01 | Statuskommunikation | Telefonische Statusanfragen erzeugen vermeidbaren Kommunikationsaufwand. |
| H02 | Transparenz | Kunden möchten den Reparaturstatus online verfolgen. |
| H03 | Digitale Freigabe | Digitale Freigaben können Entscheidungen beschleunigen und Missverständnisse reduzieren. |
| H04 | Nachvollziehbarkeit | Fotos, Diagnosehinweise und klare Kosten erhöhen die Nachvollziehbarkeit. |
| H05 | Zentrale Auftragsübersicht | Eine zentrale Übersicht über Aufträge reduziert interne Rückfragen. |
| H06 | Historie | Eine digitale Fahrzeug- und Reparaturhistorie bietet Mehrwert. |

### Folie 6 – Wie entwickeln wir das?

Iterativ. Scrum-orientiert. Qualitätsbewusst.

**Scrum im Einsatz**
- 2-Wochen-Sprints
- Product Backlog
- Sprint Planning
- Kurze Stand-ups
- Review / Demo
- Retrospektive

**Zyklus „Iterativ voran“** (kurze Zyklen schaffen Wert und ermöglichen kontinuierliches Feedback)
1. Planen – Was ist das Ziel?
2. Umsetzen – Fokus im Sprint
3. Überprüfen – Review und Demo
4. Reflektieren – Retrospektive
5. Anpassen – Backlog aktualisieren

**XP-Prinzipien**
- Pair Programming
- Continuous Integration
- Code Review
- Test-First / TDD
- Refactoring

Begründung: Kurze Iterationen helfen, regelmäßig Feedback einzuarbeiten und technische Qualität früh abzusichern.

### Folie 7 – Geplanter MVP

Unser Fokus für den erfolgreichen Start.

| Kernfunktionen (MVP) | Später möglich |
|---|---|
| Login & Rollen/Rechte | Terminbuchung |
| Kunden- und Fahrzeugverwaltung | Ersatzteilstatus |
| Reparaturauftrag mit Statusworkflow | Benachrichtigungen |
| Kostenvoranschlag | Chat |
| Digitale Freigabe/Ablehnung | Dashboard/Statistiken |
| Bilder und Notizen | Rechnung |
| Kundenansicht | Qualitätscheckliste |
| Dokumentierte Reparaturhistorie | |

**Fokus P1:** Wir starten mit den Kernfunktionen, die Werkstätten im Alltag sofort weiterbringen und eine verlässliche Basis für Wachstum schaffen. *(Auf der Folie steht „verfässliche“ – Tippfehler in der Quelle.)*

*Mockup:* Reparaturauftrag #A-1024, Status Annahme → Diagnose → Freigabe → In Arbeit → Abschluss; Fahrzeug VW Golf VII, WOB-AB 123, 123.456 km; Kunde Max Mustermann; Notiz „Fehlercode P0420 – Katalysator Effizienz zu niedrig“. Mobil: „Meine Aufträge“, Status Diagnose, Button „Details ansehen“.

### Folie 8 – Tools & Technologie *(laut Folienbild, siehe Protokoll Punkt 1)*

Unser Werkzeugkasten für Entwicklung, Qualität und Zusammenarbeit.

| Bereich | Werkzeug | Einsatz |
|---|---|---|
| Frontend / App | Next.js + TypeScript | Frontend und serverseitige Logik; als Progressive Web App (PWA) konfiguriert; Kunden können die App wie eine native App auf dem Smartphone nutzen |
| Backend / DB | Supabase | Ersetzt PostgreSQL + Prisma; Datenbank als Backend-as-a-Service; Login-System (Auth); Dateispeicher (Storage) für Bilder und Kostenvoranschläge |
| Design | Figma | UI-Design; klickbare Prototypen; gemeinsame Bearbeitung im Team |
| Management | GitHub (Projects, Actions) | Code-Verwaltung; Ticket-Board für Sprint-Planung; GitHub Projects zur Aufgabenverwaltung; CI-Pipeline mit GitHub Actions (automatisierte Tests) |

Fazit: Der ausgewählte Stack unterstützt eine effiziente Entwicklung, hohe Qualität und eine gute Zusammenarbeit innerhalb der zweiwöchigen Sprints.

> **Veraltete Textebene (nur zur Nachvollziehbarkeit):** Requirements: GitHub Issues + User Stories · Projektmanagement: GitHub Projects · Prototyp/UX: Figma · Architektur: draw.io / diagrams.net · Entwicklung: VS Code + GitHub · Web-Stack: Next.js + TypeScript · Datenbank: PostgreSQL + Prisma · Test & Qualität: Jest/Vitest, Playwright, ESLint, Prettier, GitHub Actions · Organisation: Clockify · „Der finale Stack wird im Team bestätigt und bei Bedarf pragmatisch angepasst.“

### Folie 9 – Feedback & Validierung

| Phase | Name | Wer | Methode |
|---|---|---|---|
| 1 | Problemvalidierung | 2–3 Werkstattpersonen | 15–20 min. Interviews |
| 2 | Kundensicht | 5–10 Fahrzeugkunden | Kurze Interviews oder Umfrage |
| 3 | Prototypentest | 2 Werkstattpersonen + 3 Kunden | mit klickbarem Figma-Prototyp |
| 4 | Zwischenversion | Mindestens 2 reale Nutzer/Experten | Demo und geführter Test |
| 5 | End-User-Test | 3–5 reale Personen | Szenario-basierter Nutzertest |

**Priorisierter Erstkontakt:** Norden Auto & Service (N.A.S) in Wallsbüll
**Ziel:** Hypothesen prüfen, Anforderungen ableiten und Produkt am realen Bedarf ausrichten.

### Folie 10 – Das Team

| Person | Rolle | Aufgaben |
|---|---|---|
| Parisa | Requirements & Management | Interviews & Anforderungen; Projektboard und Koordination; Feedback-Dokumentation |
| Mohammad | Quality Assurance | Testplanung & Testfälle; Fehlerdokumentation & -tracking; Code Reviews & Qualitätskontrolle |
| Khaled | Implementation | Technische Umsetzung; Programmierung der Features; Integration & Fehlerbehebung |
| Sami | Architecture & Design | Systemarchitektur & Datenmodell; Technisches Design & Schnittstellen; UI-/Prototyp-Konzeption |

Leitsatz: Klare Verantwortlichkeiten, frühes Feedback und ein fokussierter MVP sind entscheidend für den Projekterfolg.

### Folie 11 – Quellen

- Kursbeschreibung: Software-Projekt – Wintersemester 2026/27, Hochschule Flensburg, insbesondere P1 – Idee & Team.
- Schwaber, K.; Sutherland, J. (2020): The Scrum Guide. https://scrumguides.org/scrum-guide.html
- Project Management Institute & Agile Alliance (2017): Agile Practice Guide. Abschnitt A3.3 Extreme Programming. https://www.agilealliance.org/wp-content/uploads/2021/02/AgilePracticeGuide.pdf
- KI-Nutzung: Generative KI wurde unterstützend zur Erstellung einzelner visueller Elemente und Illustrationen eingesetzt.

---
## 2. Vorlesung L01 – Software Engineering Projekt: Tips und Übersicht

*Quelle: `L01_Projekt_Tips_WS26_27_key.pdf` (19 Folien) · Kai Petersen, Hochschule Flensburg*

### Folie 2 – Agenda

- Übersicht über Aufgabe
- Arbeiten im Team
- Recap
  - Anforderungen
  - Architektur und Design
  - Software testen
- Beispiele für unterstützende Anwendungen
- Plangetrieben vs. Agil

### Folien 3–5 – Lernziele

**Spezifische Lernziele (Software-Projekt)**

| ID | Lernziel |
|---|---|
| SZ1 | Fähigkeit zur **Vervollständigung eines Softwareprojektes** in einem Team mit Spezifikation von Anforderungen, Architektur, Implementierung und Test. |
| SZ2 | Fähigkeit zur Erstellung eines **Projektplans** (Schätzungen, Priorisierung von Aufgaben, Identifikation von Risiken). |
| SZ3 | Fähigkeit zur Erstellung eines **Post-Mortem** mit Problemidentifikation und der Fähigkeit, Lösungsstrategien zu formulieren. |
| SZ4 | Fähigkeit zur Nutzung von **Projektmanagementwerkzeugen** und Reflektion über diese Werkzeuge. |

**Generische Fähigkeiten**

| ID | Fähigkeit |
|---|---|
| GZ1 | Fähigkeit zur Arbeit in einem Team |
| GZ2 | Fähigkeit zum kritischen Denken |
| GZ3 | Fähigkeit zur Informationssuche |
| GZ4 | Problemlösungsfähigkeit |

### Folie 6 – Ihr erstellt ein Softwaresystem inklusive aller Kernaktivitäten und deren Ergebnisse

Erstellung einer Software in einem Entwicklungsteam:
- Durchführung der **Schlüsselaktivitäten** (Anforderungen, Architektur, Implementierung und Test) als auch die **Planung** des Projektes
- Regelmäßiger Austausch des Projektfortschritts (Scrum):
  - Was ist letzte Woche passiert?
  - Was ist für nächste Woche geplant?
  - Welche Probleme gibt es?

> Tipp: Eigene Reflexionen („Lessons Learnt“) während des Projektes notieren.

### Folie 7 – Kriterien Softwareprojekt

- Plan für das Projekt ist dokumentiert (beispielsweise Iterationsplan und Schätzungen) und ist nachvollziehbar.
- Die Auswahl und Verfolgung von Praktiken und Methoden im Software-Engineering ist sichtbar (kein „Cowboy-Programming“, ad-hoc Entwicklung). Beispiel: Wenn User Stories für die Anforderungsdokumentation gewählt wurden, wurde diese konsequent umgesetzt.
- Selbständige Erarbeitung weiterführender notwendiger Kenntnisse für den Projekterfolg.
- Abweichungen vom Plan führen zur Plananpassung.
- Kontinuierliches Vorantreiben des Projektes ist sichtbar.
- Folgende Artefakte wurden erstellt: Anforderungen, Architektur, Implementierung, Software Tests, Projektmanagement-Doku.
- Artefakte sind stimmig zueinander.

### Folie 8 – Erster Schritt

- Was soll im Projekt gemacht werden?
- Wer ist im Team und übernimmt welche Rolle (4–6 Personen)?
- Beachtet auf Moodle die Hinweise zu den verpflichtenden Präsentationen (Noten: Bestanden / Nicht bestanden)!

### Folien 9–10 – Arbeiten im Team: Rollen

| Rolle | Aufgabe |
|---|---|
| Software tester | Testet die SW |
| Requirements engineer | Sammelt, dokumentiert und stimmt Anforderungen ab |
| Team lead | Manager, Ansprechpartner |
| Architekt | Systemstruktur und Verhalten |
| Coder | Implementiert SW-System |
| … | |

### Folie 11 – Strukturierung des Teams

Fragestellungen:
- Welche Rollen?
- Eine oder mehrere Rollen im Projekt pro Person?
- Jede Aktivität hat einen „Leader“ – der Leader muss nicht alle Aufgaben in der Aktivität übernehmen. Clevere Arbeitsteilung!
- Wer trifft Entscheidungen? Demokratisch vs. Team-lead
  - Technische Entscheidungen (z. B. Architekturstil)
  - Management-Entscheidungen (z. B. Änderung Zeitplan, Budget)

### Folie 12 – Wichtige Fähigkeiten im Team bei der Themen- und Technologieauswahl

- Domänenwissen (z. B. Anwendung im Finanzwesen)
- Technische Fähigkeiten (z. B. Programmierung, Tools)
- Management-Fähigkeiten
- etc.

### Folien 13–15 – Landkarten: Anforderungen

| Deutsch | Englisch |
|---|---|
| **Kernaktivitäten:** Gewinnung, Dokumentation, Übereinstimmung | Elicitation, Specification, Negotiation |
| **Anforderungsartefakte:** Ziele, Szenarien, lösungsorientierte Anforderungen | Goals, Scenarios, Solution-oriented requirements |
| **Querschnitt:** Validierung, Management | Validation, Management |
| **Kontext-Facetten:** Gegenstandsfacette, Nutzungsfacette, IT-System-Facette, Entwicklungsfacette | – |

*(Folie 15 wiederholt Folie 14 mit englischen Begriffen.)*

### Folie 16 – Architektur

Entscheidungen, gesteuert durch **Quality Attributes**:

| Systemstruktur und Stile | Prozess |
|---|---|
| Client-Server | Agiler Architekturprozess |
| Layered | Dokumentationsart |
| Pipes & Filters | Analyse & Evaluation |
| Modular decomposition | |
| Object orientation | |

### Folie 17 – Software-Qualitätssicherung

- **Static**
  - Manual: Reviews, Walkthroughs, Inspections
  - Automated: Static Analysis
- **Dynamic**
  - Structure-Based: Statement, Decision, Condition, Path, Data-flow

### Folien 18–19 – Werkzeuge

- Versions- und Konfigurationsmanagement: **GitHub**

> Die in der Agenda genannten Punkte „Beispiele für unterstützende Anwendungen“ und „Plangetrieben vs. Agil“ sind in der Datei nicht als Folien enthalten.

---
## 3. Kursbeschreibung Software-Projekt – Wintersemester 2026/27

*Quelle: `Software_Project_WS_2026_27.pdf` (12 Seiten) · wortgetreu übernommen, nur Zeilenumbrüche und Tabellen neu gesetzt*

**Software-Projekt** – Kursbeschreibung – Wintersemester 2026/27
Kai Petersen • kai.petersen@hs-flensburg.de · Hochschule Flensburg

In diesem Kurs entwickelt ihr im Team ein Software-Produkt – und zwar aus der Perspektive eines Startups. Ihr schlüpft in die Rolle eines Gründungsteams, das eine eigene Produktidee verfolgt, echte potenzielle Kundinnen und Kunden bzw. Expertinnen und Experten anspricht und deren Feedback systematisch in die Entwicklung einbezieht. Im Folgenden werden die Lernziele, die zu treffenden Entscheidungen, der Ablauf mit verpflichtenden Präsentationen sowie die Bewertungskriterien beschrieben.

### 1 Lernergebnisse

Die Studierenden wenden die im Modul „Software Engineering“ erlernten Methoden an, um ein komplexes Software-Produkt mit agilen Entwicklungsmethoden im Team zu entwickeln. Die Entwicklung umfasst:

- Erhebung und Dokumentation von Anforderungen
- Spezifikation der Systemarchitektur
- Implementierung der Software
- Testen der Software
- Durchführung eines Post-Mortem (Retrospektive)

Die Studierenden wählen Prozesse und Methoden aus und begründen ihre Auswahl. Der Schwerpunkt liegt auf agilen Entwicklungspraktiken. Sie vergleichen Prozesse (z. B. verschiedene Ansätze und Praktiken aus Scrum, Extreme Programming und DevOps) und reflektieren diese kritisch.

Neu in dieser Ausprägung des Kurses ist die **Startup-Perspektive**: Die Studierenden lernen, eine Produktidee an realen Bedürfnissen auszurichten, indem sie Feedback von echten potenziellen Kundinnen, Kunden oder Fachexpertinnen und -experten einholen, auswerten und nachvollziehbar in die weitere Entwicklung einfließen lassen.

### 2 Die Startup-Situation: Produktidee und Kundenfeedback

Anders als in einem klassischen Auftragsprojekt gibt es keinen vorgegebenen Kunden. Euer Team agiert als Startup und muss selbst herausfinden, für wen und wofür Euer Produkt einen Wert schafft.

#### 2.1 Eure Produktidee

Euer Team wählt eine eigene Produktidee. Diese sollte ein reales Problem adressieren und in der zur Verfügung stehenden Zeit prototypisch bis zu einer lauffähigen Version umsetzbar sein. Zu Beginn formulieren Sie klar:

- Welches Problem löst ihr und für wen (Zielgruppe/Kundensegment)?
- Was ist das Wertversprechen (Value Proposition)?
- Welche Annahmen (Hypothesen) liegen der Idee zugrunde?

#### 2.2 Reale Kundinnen, Kunden und Expertinnen/Experten

Ihr müsst echte potenzielle Kundinnen und Kunden bzw. Fachexpertinnen und -experten identifizieren und aktiv ansprechen. Das können z. B. Nutzerinnen und Nutzer der Zielgruppe, Personen aus der Branche, oder Fachleute mit einschlägiger Erfahrung sein. Reine Selbstannahmen im Team genügen nicht.

> **Feedback ist verpflichtend**
> Über die gesamte Projektlaufzeit muss Euer Team kontinuierlich Feedback von realen Personen einholen und dokumentieren. Feedback wird nicht nur einmal am Anfang gesammelt, sondern begleitet die Entwicklung: Anforderungen, Prototypen, Zwischenstände und die lauffähige Software werden mit realen Personen überprüft. Dokumentiert jeweils: Wer wurde befragt (Rolle/Bezug zur Zielgruppe, keine sensiblen personenbezogenen Daten nötig), wie (Interview, Test, Umfrage), was war das Ergebnis, und welche Konsequenz hatte das Feedback für das Produkt.

#### 2.3 Umgang mit Feedback

Das gesammelte Feedback muss nachvollziehbar in Entscheidungen münden. Zeigt die Traceability: von einer Feedback-Aussage über eine abgeleitete Anforderung oder Änderung bis zur Umsetzung im Produkt. In den Präsentationen (siehe unten) legt ihr dar, welches Feedback ihr erhalten habt und wie es Ihre Produktentwicklung beeinflusst hat.

### 3 Zu treffende Entscheidungen

Im Projekt trefft ihr eine Reihe von Entscheidungen.

#### 3.1 Wie verteilen wir die Verantwortlichkeiten im Team?

Unterschiedliche Teammitglieder übernehmen die Hauptverantwortung für verschiedene Rollen und die zugehörigen Arbeitsergebnisse. Folgende Verantwortlichkeiten sind zu verteilen:

**Anforderungen (Requirements)**
Verantwortlich dafür, dass Anforderungen von realen Kundinnen/Kunden bzw. Expertinnen/Experten erhoben (z. B. durch Interviews), dokumentiert (z. B. als User Stories, Anforderungsmodelle oder natürlichsprachliche Anforderungen) und validiert werden (z. B. Feedback-Sitzungen zu Prototypen und Mock-ups). Hauptergebnis: (a) Beschreibung, wie Requirements Engineering und Feedback-Erhebung durchgeführt wurden, und (b) die Dokumentation der Anforderungen inkl. Feedback-Herkunft.

**Systemarchitektur und Entwurf (Architecture & Design)**
Verantwortlich für die Strukturierung des Systems: Komponenten und ihre Interaktionen (z. B. Komponentendiagramme), das Systemverhalten (z. B. Sequenz- und Aktivitätsdiagramme), die Struktur (z. B. UML-Klassendiagramme) sowie Datenmodelle (z. B. ER-Diagramme). Hauptergebnis: (a) Begründung der Wahl von Modelltypen und Beschreibungssprachen, (b) Architektur, Detailentwurf und Datenmodell.

**Implementierung (Implementation)**
Verantwortlich dafür, dass die Anforderungen durch die Implementierung erfüllt werden, inkl. Implementierungsdokumentation und der Definition und Einhaltung von Coding-Guidelines. Hauptergebnis: der Quellcode und dessen Dokumentation.

**Software-Qualitätssicherung (Quality Assurance)**
Verantwortlich für die Sicherung der Softwarequalität: Definition und Implementierung wiederholbarer Testfälle (manuell und/oder automatisiert, z. B. Unit-Tests) sowie Reviews/Inspektionen der Artefakte. Hauptergebnis: Testfälle, Inspektions-Guidelines und Testergebnisse. Testergebnisse dokumentieren bestandene/fehlgeschlagene Testfälle und gefundene Defekte, die als Tickets nachverfolgt werden (z. B. in GitHub/GitLab/Jira).

**Software-Management (Management)**
Verantwortlich für Planung, Überwachung, Steuerung und Dokumentation des Projektfortschritts sowie die Bereitstellung der Entwicklungsinfrastruktur (z. B. Versionsverwaltung). Hauptergebnis: ein Reflexionsdokument mit (a) den eingesetzten Praktiken, (b) was gut/schlecht lief, (c) Verbesserungsideen und (d) Projektstatistiken. Statistiken enthalten: (a) den Aufwand je Teammitglied nach Aktivität (Requirements, Architektur, Implementierung, QA, Management) und (b) eine Analyse der Produktivität (Anzahl/Frequenz der Commits, Codezuwachs über die Zeit, Hauptbeitragende je Datei).

> **Hinweis zur Rollenverteilung**
> Ist eine Person für eine Aktivität verantwortlich, heißt das nicht, dass sie die einzige ist, die daran arbeitet! Die Verantwortung bezieht sich auf Koordination und Vollständigkeit des Arbeitsergebnisses. Zu Projektbeginn reicht jedes Team eine Beschreibung der geplanten Rollenverteilung ein.

#### 3.2 Welche Lebenszyklusmodelle und Praktiken werden verwendet?

Beispiele für Lebenszyklusmodelle: Wasserfall/planbasiert; agile Entwicklung (z. B. Scrum, Extreme Programming). In der Praxis werden Modelle häufig durch Kombination von Praktiken (etwas Scrum, etwas plan-driven, etwas XP) an den Bedarf angepasst. Beispiele für Praktiken: Product Backlog, Sprints, Pair Programming, Test-Driven Development, Standup-Meetings, User Stories, Planning Game.

#### 3.3 Welche Entwicklungsumgebung und Werkzeuge?

> **Sehr wichtig**
> Nutzt eine Programmiersprache und Entwicklungsumgebung, mit der ihr vertraut seid. Ziel des Kurses ist es, den gesamten Entwicklungsprozess von der Anforderungsspezifikation über das Testen bis zur Auslieferung zu erleben. Eine neue Sprache kostet zusätzlichen Aufwand und lenkt vom eigentlichen Lernziel ab.

### 4 Verbindliche Anforderungen an das Projekt

- Ihr führt alle zentralen Aktivitäten der Softwareentwicklung durch (siehe oben) und dokumentiert jede Aktivität.
- Ihr holt kontinuierlich Feedback von realen Kundinnen/Kunden bzw. Expertinnen/Experten ein und dokumentiert es.
- Ein Konfigurationsmanagement-Werkzeug wird eingesetzt (z. B. GitHub). Die Historie muss verfügbar und nachvollziehbar sein (wer hat wann was committet). Auch Analysen des eigenen Projektes sollen durchgeführt werden (z.B. Produktivität, Aktivitäten des Teams im Projekt, Aufwände)
- Nutzt Projekt-Tracking (Ticket-/Board-System wie Jira, Trello, GitHub Projects o. ä.), das den Fortschritt jederzeit sichtbar macht.

> **Abgabe der Software**
> Die Software und alle relevanten Dokumente für jede Aktivität sollen über einen Github-Link abgegeben werden. Zusätzlich muss eine lauffähige Version bereitstehen – entweder online gehostet (z. B. über GitHub Pages, einen Hosting-Dienst o. ä.) oder als direkt lauffähige Desktop-Anwendung. Bewertet wird an der Rubrik (siehe unten); Voraussetzung für die Abgabe ist das Bestehen aller verpflichtenden Präsentationen.

### 5 Ablauf, Präsentationen und Projekt-Tracking

Die Veranstaltung findet mittwochs, 08:15–11:30 Uhr, in Raum C229 statt. Alle zwei Wochen präsentiert jedes Team einen Zwischenstand.

> **Regeln für die Präsentationen**
> - Die Präsentationen sind verpflichtend und werden mit Bestanden / Nicht bestanden bewertet.
> - Zu jeder Präsentation gibt es Feedback (von Lehrenden und ggf. Peers).
> - Der Projektfortschritt muss klar erkennbar sein: Was war geplant, was wurde erreicht, was kommt als Nächstes, welche Risiken bestehen?
> - Das Bestehen aller Präsentationen ist Voraussetzung für die Abgabe des Projekts.

Zeigt in jeder Präsentation den Stand des Projekt-Trackings (Board/Tickets, Burndown/Fortschritt, Commit-Aktivität) und – ab dem Zeitpunkt der Erhebung – das gesammelte Kundenfeedback und dessen Konsequenzen.

#### 5.1 Wochenplan

| Datum | Termin | Aktivität / Deliverable |
|---|---|---|
| 23.09.2026 | Kick-Off | Einführung in den Kurs. Vorstellung des Kurses. |
| 30.09.2026 | P1 (Pflicht) | **Präsentation 1 – Idee & Team.** Vorstellung der Produktidee, Zielgruppe, Wertversprechen und Hypothesen. Rollenverteilung im Team, gewähltes Lebenszyklusmodell und Praktiken (begründet), geplante Werkzeuge. Plan zur Ansprache realer Kundinnen/Kunden/Expertinnen. |
| 07.10.2026 | Arbeit & Q&A | Arbeitszeit; erste Kunden-/Expertengespräche vorbereiten und starten, Interviewleitfaden erstellen. |
| 14.10.2026 | P2 (Pflicht) | **Präsentation 2 – Anforderungen & erstes Feedback.** Ergebnisse der Erhebung, dokumentierte Anforderungen, erstes reales Feedback und dessen Einfluss. Skizze der Systemstruktur. |
| 21.10.2026 | Arbeit & Q&A | Arbeitszeit; Prototypen bauen, Anforderungen verfeinern, Architektur skizzieren, erste Tests entwerfen. |
| 28.10.2026 | P3 (Pflicht) | **Präsentation 3 – Architektur & Prototyp.** Systemarchitektur (mit Begründung), Datenmodell, lauffähiger Prototyp/Zwischenversion. Fortschritt im Tracking sichtbar. |
| 04.11.2026 | Arbeit & Q&A | Arbeitszeit; Implementierung ausbauen, Feedback einholen. |
| 11.11.2026 | P4 (Pflicht) | **Präsentation 4 – Implementierung & Feedback-Runde.** Demo des aktuellen Stands, Fortschritt seit P3, weiteres reales Feedback und abgeleitete Änderungen. Teststand. |
| 18.11.2026 | Arbeit & Q&A | Arbeitszeit. |
| 25.11.2026 | P5 (Pflicht) | **Präsentation 5 – Qualität & Tests.** Testfälle auf mehreren Ebenen, Testergebnisse, Reviews/Inspektionen, dokumentierte Defekte. Fortschritt sichtbar. |
| 02.12.2026 | Arbeit & Q&A / Nutzertests | Arbeitszeit; End-User-Tests der Software mit realen Personen durchführen. |
| 09.12.2026 | P6 (Pflicht) | **Präsentation 6 – Nutzertests & Reifegrad.** Ergebnisse der End-User-Tests, Konsequenzen, Stand der lauffähigen Software (online oder Desktop). |
| 16.12.2026 | P7 + Abgabe | **Präsentation 7 – Abschluss & Übergabe.** (a) Demo der lauffähigen Software, (b) Diskussion der Qualität (Testergebnisse), (c) Reflexion (was lief gut, was anders?). Projektabgabe (siehe unten). |

> **Checklisten je Präsentation**
> Für jede Präsentation gilt die allgemeine Checkliste; zusätzlich ist die zum jeweiligen Schwerpunkt passende Checkliste aus Abschnitt 6 zu erfüllen. Ein „Bestanden“ setzt voraus, dass die allgemeine Checkliste vollständig und die schwerpunktbezogene Checkliste im Wesentlichen erfüllt ist.

### 6 Präsentations-Checklisten (Bestehen)

#### 6.1 Allgemeine Checkliste (jede Präsentation)
- [ ] Ziel und Inhalt der Präsentation sind klar; alle Teammitglieder sind eingebunden.
- [ ] Projektfortschritt ist nachvollziehbar dargestellt: Geplant vs. Erreicht, nächste Schritte, Risiken/Blocker.
- [ ] Projekt-Tracking wird gezeigt (Board/Tickets, Commit-Aktivität, Fortschrittsindikatoren).
- [ ] Kundenfeedback seit der letzten Präsentation wird dargestellt (wer, wie, Ergebnis) inkl. abgeleiteter Konsequenzen (ab Erhebungsbeginn).
- [ ] Offene Fragen und Entscheidungsbedarf sind benannt.

#### 6.2 P1 – Idee & Team
- [ ] Produktidee, Problem, Zielgruppe und Wertversprechen sind klar.
- [ ] Zentrale Hypothesen/Annahmen sind explizit.
- [ ] Rollenverteilung im Team ist festgelegt.
- [ ] Lebenszyklusmodell und Praktiken sind gewählt und begründet.
- [ ] Werkzeuge (Requirements, Entwurf, Implementierung, Test, Management) sind benannt.
- [ ] Plan zur Ansprache realer Kundinnen/Kunden/Expertinnen liegt vor.

#### 6.3 P2 – Anforderungen & erstes Feedback
- [ ] Vorgehen der Anforderungserhebung ist beschrieben.
- [ ] Anforderungen sind detailliert, testbar und mit gewählter Notation dokumentiert (mehr als nur 10–12 abstrakte User Stories).
- [ ] Rationale und Stakeholder je Anforderung sind erkennbar (Pre-Traceability).
- [ ] Erstes reales Feedback wurde eingeholt und dessen Einfluss dargestellt.

#### 6.4 P3 – Architektur & Prototyp
- [ ] High-Level-Struktur (Komponenten, Konnektoren) ist modelliert, Verhalten skizziert.
- [ ] Detailentwurf (z. B. Klassendiagramme) und Datenmodell sind vorhanden.
- [ ] Architekturentscheidung ist begründet (z. B. Architekturstil).
- [ ] Traceability Anforderung → Realisierung ist erkennbar.
- [ ] Ein lauffähiger Prototyp wird demonstriert.

#### 6.5 P4 – Implementierung & Feedback-Runde
- [ ] Demo zeigt Funktionsfortschritt seit P3.
- [ ] Implementierung ist konsistent mit Architektur/Entwurf und gut strukturiert.
- [ ] Coding-Standards sind vereinbart und werden eingehalten.
- [ ] Commits sind kontinuierlich und auf mehrere Teammitglieder verteilt.
- [ ] Weiteres reales Feedback und abgeleitete Änderungen sind dargestellt.

#### 6.6 P5 – Qualität & Tests
- [ ] Testfälle auf mehreren Ebenen (Unit, Komponente, Akzeptanz) sind definiert.
- [ ] Testfälle sind wiederholbar/ausführbar (Inputs und Test-Orakel klar).
- [ ] Review-/Inspektions-Guidelines liegen vor.
- [ ] Test- und Review-Ergebnisse sind dokumentiert (bestanden/fehlgeschlagen, Bug-Beschreibungen).

#### 6.7 P6 – Nutzertests & Reifegrad
- [ ] End-User-Tests mit realen Personen wurden durchgeführt.
- [ ] Ergebnisse und abgeleitete Konsequenzen sind dargestellt.
- [ ] Eine lauffähige Software (online oder Desktop) wird gezeigt.
- [ ] Fortschritt und verbleibende Aufgaben bis zur Abgabe sind klar.

#### 6.8 P7 – Abschluss & Übergabe
- [ ] Demo der finalen, lauffähigen Software.
- [ ] Qualitätsdiskussion (Testergebnisse) ist fundiert.
- [ ] Reflexion (was lief gut/schlecht, was anders?) ist vorhanden.
- [ ] Vollständige Projektabgabe ist bereit (siehe Abgabe).

### 7 Bewertungs-Checklisten (inhaltlich)

#### 7.1 Anforderungen
- Anforderungen sind so detailliert, dass Außenstehende sie verstehen und umsetzen könnten.
- Rationale (Warum gibt es die Anforderung?) ist dokumentiert.
- Eine geeignete Notation/Modellierung wird verwendet; Anforderungen sind testbar.
- Stakeholder sind klar; Pre-Traceability (Quelle der Anforderung, inkl. Feedback-Herkunft) ist gegeben.
- Anforderungen werden aktiv erhoben und validiert.

#### 7.2 Architektur und Entwurf
- High-Level-Struktur (Module, Konnektoren) und Verhalten sind modelliert.
- Detailebene: Struktur (Klassendiagramme) und Verhalten (Aktivitäts-/Sequenzdiagramme).
- Architekturwahl ist begründet; Traceability Anforderung → Realisierung.
- Schnittstellen sind klar definiert; Notation konsistent und korrekt.
- Gute Entwurfsprinzipien (Modularisierung, Information Hiding, lose Kopplung, hohe Kohäsion).

#### 7.3 Implementierung
- Implementierung ist konsistent mit Architektur/Entwurf.
- Projekt ist gut strukturiert (kein Monolith in einer Datei).
- Quellcode ist gut dokumentiert (Ein-/Ausgaben, Rolle einer Klasse erkennbar).
- Coding-Standards sind vereinbart, begründet und durchgesetzt.
- Kontinuierliche Commits; Arbeit auf mehrere Teammitglieder verteilt.

#### 7.4 Testen
- Testfälle auf mehreren Ebenen (Unit, Komponente, Akzeptanz).
- Testfälle sind wiederholbar/ausführbar; Inputs und Orakel klar bzw. Tests implementiert.
- Material/Guidelines für Reviews und Inspektionen sind definiert.
- Test- und Review-Ergebnisse sind dokumentiert; kontinuierliche Tests.

#### 7.5 Management
- Wahl der Praktiken/Methoden ist beschrieben und begründet.
- Definierte Methoden werden nachweislich eingehalten (in Arbeitsprodukten sichtbar).
- Projekt schreitet kontinuierlich voran (keine Last-Minute-Arbeit).
- Probleme werden benannt; Lösungen sind nachvollziehbar zugeordnet.
- Literatur (z. B. Google Scholar) stützt Entscheidungen; Fortschritt ist über Versionierung/Board nachvollziehbar.

### 8 Bewertungsrubrik des Projekts

Das abgegebene Projekt wird anhand der folgenden Rubrik bewertet. Jede der fünf Kategorien enthält vier Kriterien, die auf einer vierstufigen Skala bewertet werden:

**0 – Ungenügend · 1 – Ausbaufähig · 2 – Ausreichend · 3 – Vorbildlich**

Pro Kategorie sind maximal 12 Punkte erreichbar, insgesamt 60 Punkte. Voraussetzung für die Bewertung ist das Bestehen aller verpflichtenden Präsentationen.

#### Anforderungen (Requirements) – Erreichbar: 12 Punkte

| Kriterium | 0 – Ungenügend | 1 – Ausbaufähig | 2 – Ausreichend | 3 – Vorbildlich |
|---|---|---|---|---|
| Detailgrad & Klarheit | Anforderungen sind wenig detailliert und für Außenstehende nicht verständlich. | Etwas detailliert, aber nicht durchgehend klar. | Detailliert und für Außenstehende klar. | Außergewöhnlich detailliert, klar und gut verständlich. |
| Anforderungs-Notation | Unpassende oder inkonsistente Notation. | Teilweise passend und gelegentlich konsistent. | Passende Notation, überwiegend konsistent. | Durchgängig passend und konsistent eingesetzt. |
| Dokumentationsformen | Nur eine Form, ohne Tiefe. | Mehrere Formen, aber nicht komplementär. | Mehrere Formen effektiv genutzt. | Vielfältige, komplementäre Formen für umfassendes Verständnis. |
| Erhebung & Validierung | Kaum Belege für Erhebung/Validierung. | Etwas aktive Erhebung und Validierung. | Klare Belege aktiver Erhebung und Validierung. | Umfassende, systematische Erhebung und Validierung. |

#### Architektur und Entwurf (Architecture & Design) – Erreichbar: 12 Punkte

| Kriterium | 0 – Ungenügend | 1 – Ausbaufähig | 2 – Ausreichend | 3 – Vorbildlich |
|---|---|---|---|---|
| High-Level-Struktur | Nicht oder unklar modelliert. | Modell oberflächlich ohne geeignete Notation. | Mit angemessenem Detail und geeigneter Notation modelliert. | Umfassend modelliert, inkl. struktureller und Verhaltensaspekte. |
| Detailentwurf | Struktur bzw. Verhalten fehlen. | Einige Detailspezifikationen vorhanden. | Detailentwurf weitgehend vollständig. | Gründlich spezifiziert, klare Struktur und Verhalten. |
| Begründung der Architektur | Keine Begründung der Entscheidungen. | Einige Begründungen vorhanden. | Klare Begründung der meisten Entscheidungen. | Gründliche, überzeugende Begründung aller Entscheidungen. |
| Entwurfsprinzipien | Kaum Beachtung guter Prinzipien. | Teilweise Beachtung. | Überwiegend Beachtung guter Prinzipien. | Vorbildliche Beachtung aller guten Prinzipien. |

#### Implementierung (Implementation) – Erreichbar: 12 Punkte

| Kriterium | 0 – Ungenügend | 1 – Ausbaufähig | 2 – Ausreichend | 3 – Vorbildlich |
|---|---|---|---|---|
| Projektstruktur | Schlecht, große monolithische Teile. | Etwas strukturiert, nicht durch Entwurf erzwungen. | Gut strukturiert, durch guten Entwurf getragen. | Hervorragend strukturiert, modular und sauber. |
| Doku aus Code | Quellcode ohne Dokumentation. | Etwas dokumentiert. | Gut dokumentiert. | Außergewöhnlich gut dokumentiert, fördert Verständnis/Nutzung. |
| Coding-Standards | Keine Einhaltung. | Etwas Einhaltung vereinbarter Standards. | Überwiegend Einhaltung begründeter Standards. | Vollständige Einhaltung begründeter, durchgesetzter Standards. |
| Konsistenz zur Architektur | Implementierung spiegelt Architektur nicht wider. | Teilweise Übereinstimmung. | Konsistent mit Architektur/Entwurf. | Spiegelt Architektur/Entwurf perfekt wider. |

#### Testen (Testing) – Erreichbar: 12 Punkte

| Kriterium | 0 – Ungenügend | 1 – Ausbaufähig | 2 – Ausreichend | 3 – Vorbildlich |
|---|---|---|---|---|
| Definition der Testfälle | Schlecht definiert oder fehlend. | Definiert, aber wenig detailliert. | Gut definiert über mehrere Ebenen. | Außergewöhnlich detailliert und umfassend über alle Ebenen. |
| Testausführung | Nicht wiederholbar/ausführbar. | Einige wiederholbar/ausführbar. | Meist wiederholbar/ausführbar. | Alle wiederholbar, ausführbar und klar dokumentiert. |
| Reviews & Inspektionen | Kein Material/keine Guidelines. | Etwas Material ohne klare Guidelines. | Material mit klaren Guidelines. | Umfassendes Material mit detaillierten Guidelines. |
| Ergebnisdok. | Ergebnisse nicht dokumentiert. | Einige Ergebnisse dokumentiert. | Ergebnisse überwiegend dokumentiert. | Alle Ergebnisse gründlich dokumentiert, mit klaren Bug-Beschreibungen. |

#### Management – Erreichbar: 12 Punkte

| Kriterium | 0 – Ungenügend | 1 – Ausbaufähig | 2 – Ausreichend | 3 – Vorbildlich |
|---|---|---|---|---|
| Entwicklungspraktiken | Nicht beschrieben/begründet. | Einige beschrieben und begründet. | Meiste klar beschrieben und begründet. | Alle gründlich beschrieben, begründet und in Arbeitsprodukten sichtbar. |
| Kontinuierlicher Fortschritt | Zeichen von Last-Minute-Arbeit. | Fortschritt in Etappen, teils kontinuierlich. | Stetiger, kontinuierlicher Fortschritt. | Vorbildlich kontinuierlich, mit detaillierten Statistiken. |
| Problemdok. | Probleme nicht dokumentiert. | Einige dokumentiert. | Meiste dokumentiert. | Alle dokumentiert, mit nachvollziehbaren Lösungen. |
| Literatur & Referenzen | Keine Nutzung von Literatur. | Einige Referenzen zur Stützung. | Meiste Entscheidungen durch Literatur gestützt. | Alle Entscheidungen stark durch Literatur/Referenzen gestützt. |

#### Punktevergabe & Note

Gesamtpunktzahl: Summe der fünf Kategorien (max. 60). Der Prozentwert (erreichte / erreichbare Punkte) bildet die Grundlage der Notenermittlung. Das Bestehen aller verpflichtenden Präsentationen (Bestanden/Nicht bestanden) ist Voraussetzung für die Bewertung des Projekts.

### 9 Gruppengröße

Die Gruppengröße beträgt vier bis sechs Personen. Jedes Mitglied verantwortet eine Rolle (fünf Rollen, siehe oben). Bei sechs Personen wird eine Verantwortung von zwei Personen geteilt – empfohlen wird das Teilen der Implementierung, da diese am zeitintensivsten ist.

### 10 Projektabgabe (16.12.2026)

Die Abgabe erfolgt über Moodle (als ZIP mit allen notwendigen Details als auch per Repository-Link). Benenne die Dateien wie folgt:

- **Anforderungen:** `hauptverantwortlich_requirements.pdf`
- **Architektur & Entwurf:** `hauptverantwortlich_design.pdf`
- **Implementierung:** Ordner `hauptverantwortlich_implementation` plus Link zum Repository (GitHub/GitLab/Bitbucket).
- **Lauffähige Software:** Link zur online gehosteten Version oder eine direkt lauffähige Desktop-Anwendung inkl. kurzer Start-/Installationsanleitung.
- **Testen:** `hauptverantwortlich_testing.pdf` (Code ggf. im Ordner `hauptverantwortlich_testing`).
- **Management:** `hauptverantwortlich_management.pdf` inkl. Einladung zum Projekt-Board.
- **Feedback-Dokumentation:** Zusammenstellung des über die Laufzeit gesammelten realen Kundenfeedbacks und seiner Konsequenzen.

> **Hinweis zur Autorenschaft**
> Jedes Dokument nennt seine Autorinnen/Autoren und deren relativen Beitrag in %. Beispiel (Anforderungen): Tom (30%), Markus (30%), Lena (20%), Kris (10%), Tina (10%).

---

## 4. Abgleich: WerkstattStatus-P1 gegen die P1-Checkliste

| Checklistenpunkt P1 | Abgedeckt durch | Status |
|---|---|---|
| Produktidee, Problem, Zielgruppe, Wertversprechen | Folien 1–4 | ✅ |
| Zentrale Hypothesen explizit | Folie 5 (H01–H06) | ✅ |
| Rollenverteilung festgelegt | Folie 10 | ✅ (Parisa trägt zwei Rollen: Requirements + Management) |
| Lebenszyklusmodell und Praktiken gewählt und begründet | Folie 6, Quellen Folie 11 | ✅ |
| Werkzeuge je Bereich benannt | Folie 8 | ⚠️ Im aktuellen Folienbild fehlen explizite Test-Werkzeuge (nur „automatisierte Tests“ via GitHub Actions); die ältere Textebene nannte Jest/Vitest, Playwright, ESLint, Prettier |
| Plan zur Ansprache realer Kunden/Experten | Folie 9 (5 Phasen, Erstkontakt N.A.S Wallsbüll) | ✅ |
| Allgemein: Projekt-Tracking gezeigt | – | ⚠️ Kein Board/Commit-Stand auf den Folien sichtbar |
| Allgemein: Offene Fragen/Entscheidungsbedarf, Risiken | – | ⚠️ Keine eigene Folie zu Risiken/offenen Fragen |
