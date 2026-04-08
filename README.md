# Schritt-für-Schritt-Anleitung: Copilot-Cloud-Agent-Umgebung

Dieses Beispiel zeigt, wie du ein Node.js-Projekt mit Copilot-Cloud-Agent-Umgebung einrichtest und automatisiert testest.

## 1. Projektstruktur

```
Beispiel_cloud_agent_environment/
├── index.js
├── index.test.js
├── package.json
├── README.md
└── .github/
    └── workflows/
        └── copilot-setup-steps.yml
```

## 2. Code und Test
- **index.js**: Enthält die Summenfunktion
- **index.test.js**: Testet die Funktion mit Jest

## 3. Abhängigkeiten
- In `package.json` sind `jest` (Test-Framework) und `axios` (Beispiel-Dependency) eingetragen.

## 4. Workflow-Datei
- `.github/workflows/copilot-setup-steps.yml` definiert die Schritte für die Cloud-Agent-Umgebung:
  - Checkt den Code aus
  - Installiert Node.js
  - Installiert alle Dependencies
  - Führt die Tests aus

## 5. Workflow ausführen
- Push das Projekt in ein GitHub-Repository.
- Gehe auf GitHub unter "Actions" und starte den Workflow "Copilot Setup Steps" manuell (workflow_dispatch).
- Der Workflow installiert alles und führt die Tests automatisch aus.

## 6. Ergebnis prüfen
- Nach Abschluss siehst du im Workflow-Log, ob die Tests erfolgreich waren.

---

**Tipp:** Du kannst die Workflow-Datei anpassen, um weitere Schritte, Umgebungsvariablen oder Services (z.B. Datenbank) hinzuzufügen.
