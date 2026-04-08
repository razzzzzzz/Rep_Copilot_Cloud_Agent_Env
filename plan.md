# Plan: Beispiel für Copilot-Cloud-Agent-Umgebung (customizing-copilot-cloud-agents-environment)

## Ziel
Anhand eines kleinen Node.js-Projekts wird gezeigt, wie die 6 Schritte zur Anpassung der Copilot-Cloud-Agent-Umgebung praktisch umgesetzt werden.

## Beispielprojekt
Ein Node.js-Projekt, das Tests mit Jest ausführt und eine zusätzliche Dependency (z.B. `axios`) benötigt.

## Schritte im Detail

1. **copilot-setup-steps.yml anlegen**
   - Lege im Projekt unter `.github/workflows/` die Datei `copilot-setup-steps.yml` an.
   - Zweck: Definiert, wie die Cloud-Umgebung für Copilot vorbereitet wird.

2. **Job "copilot-setup-steps" definieren**
   - In der YAML-Datei wird ein Job mit dem Namen `copilot-setup-steps` angelegt.
   - Zweck: Dieser Job wird von Copilot genutzt, um die Umgebung einzurichten.

3. **runs-on, steps, permissions, services, snapshot, timeout-minutes anpassen**
   - `runs-on`: Wähle den passenden Runner (z.B. `ubuntu-latest` für Node.js).
   - `steps`: Installiere Node.js, Dependencies, führe Tests aus.
   - `permissions`: Setze Berechtigungen, falls z.B. auf Secrets zugegriffen wird.
   - `services`: Definiere z.B. eine Datenbank, falls benötigt.
   - `snapshot`: Optional, um einen Zustand zu speichern.
   - `timeout-minutes`: Setze ein Zeitlimit für den Job.

4. **Tools/Dependencies installieren**
   - Füge in `steps` z.B. `npm install` und `npm install axios` ein.
   - Zweck: Stellt sicher, dass alle benötigten Pakete verfügbar sind.

5. **Runner anpassen**
   - Falls spezielle Anforderungen bestehen (z.B. Windows), ändere `runs-on` entsprechend.
   - Zweck: Die Umgebung passt sich dem Projektbedarf an.

6. **Umgebungsvariablen setzen**
   - Lege in GitHub unter Settings > Environments eine Umgebung (z.B. `copilot`) an.
   - Setze dort benötigte Variablen (z.B. API-Keys).
   - Zweck: Variablen stehen im Workflow sicher zur Verfügung.

## Beispiel copilot-setup-steps.yml
```yaml
name: Copilot Setup Steps
on:
  workflow_dispatch:
jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - name: Install dependencies
        run: npm install
      - name: Install axios
        run: npm install axios
      - name: Run tests
        run: npm test
```

## Todos
- [ ] Beispielprojekt beschreiben
- [ ] Schritte 1-6 im Detail erläutern
- [ ] Beispiel-Workflow-Datei bereitstellen
- [ ] Hinweise zu Umgebungsvariablen ergänzen
