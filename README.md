# n8n: Vorlagen zu stillen Fehlern

[English version](README.en.md)
Drei kleine n8n-Workflows zu Fehlern, die keine Fehlermeldung erzeugen: der Workflow läuft grün und tut trotzdem das Falsche. Die Vorlagen stammen aus dem Betrieb von Automatisierungen bei [Bot-Agent](https://bot-agent.de) und sind bewusst klein gehalten.

| Datei | Zweck |
|---|---|
| `workflows/01-if-node-mit-combinator.json` | Webhook, If-Node mit gesetztem `combinator` und zwei Zweigen, zum Testen des Falsch-Zweigs |
| `workflows/02-umgebungsvariable-code-node.json` | Prüft in einem Code-Node, ob eine Umgebungsvariable per `$env` ankommt, ohne den Wert auszugeben |
| `workflows/03-error-workflow-meldung.json` | Error Trigger, baut einen Meldungstext (Workflow, Node, Fehler, Link zur Ausführung); Mail- oder Chat-Node selbst einsetzen |

Dazu eine [Checkliste für den Betrieb](docs/checkliste-stille-fehler.md).

## Import

In n8n: Workflows, Import from File, JSON-Datei wählen. Alle Vorlagen sind inaktiv gespeichert. Die Strukturen wurden gegen eine n8n-Instanz geprüft (Anlegen über die API). Vor dem Einsatz bitte importieren und mit eigenen Daten testen. Es gibt keine Garantie, dass sie für jede n8n-Version unverändert laufen.

## Hintergrund

Die Hintergründe zu Kosten und Betrieb stehen im Blog:

- [n8n Preise: Kosten und ROI für deutsche Unternehmen](https://blog.bot-agent.de/n8n-preise-kosten-vergleich/)
- [n8n Tutorial: Prozesse effizient automatisieren](https://blog.bot-agent.de/n8n-tutorial-prozesse-automatisieren/)

## Hinweise

- Zu `$env`: Laut n8n-Dokumentation ist der Zugriff auf Umgebungsvariablen in Nodes ab Version 2.0 standardmäßig gesperrt und muss bewusst freigegeben werden. Prüfen Sie Ihre Version und Konfiguration.
- Zum If-Node ohne `combinator`: Das ist eine eigene Beobachtung aus dem Betrieb, in der n8n-Dokumentation nicht beschrieben. Setzen Sie `combinator` ausdrücklich.
- Die Vorlagen enthalten keine Zugangsdaten. Tragen Sie Geheimnisse nie in Nodes ein, sondern nutzen Sie Credentials oder Umgebungsvariablen.

## Lizenz

MIT, siehe `LICENSE`.
