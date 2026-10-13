# WerkstattStatus

Werkstatt-Management-System für Hochschule Flensburg (WS 2026/27).

**Stack:** Next.js + TypeScript, Supabase, GitHub (Issues, Projects, Actions)

---

## 📚 Dokumentation

### Für Agenten
- **[agent.md](./agent.md)** ← **HIER ANFANGEN** – Zentrale Guidelines für alle KI-Agenten
- [agenten/github.agent.md](./agenten/github.agent.md) – Spezifische GitHub-Workflow-Regeln für Agenten

### Für Menschen
- [docs/Git-Workflow.md](./docs/Git-Workflow.md) – Detaillierter Git-Workflow und Branch-Konzept
- [docs/Projektmanagement.md](./docs/Projektmanagement.md) – Projekt-Anforderungen und Management

---

## 🚀 Quick Start

### Code auschecken
```bash
git clone https://github.com/khaledbakourcoder/werkstattstatus.git
cd werkstattstatus/app
npm install
npm run dev
```

### Entwickeln
1. Lies zuerst [agent.md](./agent.md) (für Agenten) oder [docs/Git-Workflow.md](./docs/Git-Workflow.md) (für Menschen)
2. Erstelle einen Branch: `git switch -c feat/XX-beschreibung --no-track origin/develop`
3. Schreibe Code
4. Teste lokal: `npm run lint && npm run build`
5. Push & PR öffnen

---

## 🛠️ Projektstruktur

```
werkstattstatus/
├── app/                     ← Next.js Projekt (Node.js v22)
│   ├── app/                 ← Next.js App Router
│   ├── public/              ← Static Assets
│   ├── package.json
│   └── .nvmrc               ← Node-Version
├── .github/workflows/       ← GitHub Actions (CI/CD)
│   └── ci.yml               ← Lint, Build
├── docs/                    ← Dokumentation
│   ├── Git-Workflow.md
│   └── Projektmanagement.md
├── agenten/                 ← Agent-specific Skills
│   └── github.agent.md
├── agent.md                 ← Zentrale Agenten-Guidelines
└── README.md                ← Diese Datei
```

---

## 👥 Team

- **Khaled** (khaledbakourcoder) – Implementierung, Repo-Owner
- **Mohammad** – QA, Code Reviews
- **Parisa** – Requirements & Management
- **Sami** – Architektur & Design

---

## 🔄 Workflow

**Ticket → Branch → Commit → PR → Review → Merge**

Detailliert in [agent.md](./agent.md) und [docs/Git-Workflow.md](./docs/Git-Workflow.md).

---

## 📋 CI/CD

GitHub Actions läuft automatisch bei:
- Push auf `main` oder `develop`
- Pull Requests auf `main` oder `develop`

**Jobs:**
- ✅ Lint (ESLint)
- ✅ Build (Next.js)

---

## 📖 Weitere Infos

- GitHub: https://github.com/khaledbakourcoder/werkstattstatus
- Projektmanagement: siehe [docs/Projektmanagement.md](./docs/Projektmanagement.md)