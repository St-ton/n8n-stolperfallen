# Checkliste: stille Fehler in n8n-Workflows

Jeder Punkt beschreibt eine Beobachtung aus dem Betrieb, keine Garantie für jede Version.

1. **If-Node:** `combinator` ausdrücklich auf `and` oder `or` setzen, besonders bei per Skript oder API erzeugten Workflows. Den Falsch-Zweig mit einem Testfall prüfen, nicht nur den Erfolgsfall.
2. **Umgebungsvariablen:** In Code-Nodes `$env.NAME` statt `process.env.NAME` verwenden. Beim Umstellen zuerst mit einem Mini-Workflow prüfen, ob der Wert ankommt (nur die Länge ausgeben).
3. **Ausführungsreihenfolge:** In den Workflow-Einstellungen `executionOrder` auf `v1` setzen. Bei älteren oder importierten Workflows kontrollieren.
4. **Error-Workflow:** In jedem produktiven Workflow einen Error-Workflow hinterlegen, der eine Meldung versendet.
5. **Ausführungsverlauf:** Nach Änderungen die Execution-Historie ansehen: Welche Nodes liefen, welche Daten flossen?
6. **Testdaten:** Bewusst falsche und leere Eingaben testen.
7. **Polling:** Jedes Abfrageintervall ist eine Execution. Vergessene Polling-Workflows prüfen oder abschalten.
8. **LLM-Nodes:** Tageslimit beim Anbieter setzen, Tests mit kleinen Datenmengen fahren, einen eigenen Schlüssel je Anwendungsfall nutzen.
9. **Abgelaufene Tokens:** OAuth-Tokens und API-Schlüssel haben ein Ablaufdatum. Ohne Error-Workflow fällt ein Ausfall oft erst nach Tagen auf.
