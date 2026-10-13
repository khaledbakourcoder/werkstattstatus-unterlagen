# Ein-Klick-Setup WerkstattStatus

Voraussetzungen: Node.js (>= 20) und Git.

- Windows: Doppelklick auf `setup.cmd`
- macOS/Linux: `./setup.sh`
- Eigener Zielordner: `node setup.mjs "C:\Pfad\werkstattstatus"`

Standard-Zielordner: neben diesem Ordner, `../werkstattstatus`.
Das Skript pusht nichts. Es legt Projekt, Ordnerstruktur, CI, Vitest, Prettier an,
kopiert die Unterlagen nach `docs/quellen/` und macht einen lokalen Commit.
