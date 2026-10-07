# n8n: Templates for silent failures

Three small n8n workflows about failures that produce no error message: the workflow runs green and still does the wrong thing. The templates come from running automations at [Bot-Agent](https://bot-agent.de) and are intentionally kept small. Node labels inside the workflows are in German.

| File | Purpose |
|---|---|
| `workflows/01-if-node-mit-combinator.json` | Webhook, If node with `combinator` set and two branches, for testing the false branch |
| `workflows/02-umgebungsvariable-code-node.json` | Checks in a Code node whether an environment variable arrives via `$env`, without printing the value |
| `workflows/03-error-workflow-meldung.json` | Error Trigger, builds a message text (workflow, node, error, link to the execution); insert your own email or chat node |

Also included: a [checklist for operations](docs/checkliste-stille-fehler.md) (German).

## Import

In n8n: Workflows, Import from File, choose the JSON file. All templates are saved as inactive. The structures were checked against an n8n instance (created through the API). Please import and test them with your own data before use. There is no guarantee that they run unchanged on every n8n version.

## Background

Background on costs and operations is on the blog (German):

- [n8n Preise: Kosten und ROI für deutsche Unternehmen](https://blog.bot-agent.de/n8n-preise-kosten-vergleich/)
- [n8n Tutorial: Prozesse effizient automatisieren](https://blog.bot-agent.de/n8n-tutorial-prozesse-automatisieren/)

## Notes

- On `$env`: according to the n8n documentation, access to environment variables in nodes is blocked by default from version 2.0 and must be enabled deliberately. Check your version and configuration.
- On the If node without `combinator`: this is an own observation from operations and is not described in the n8n documentation. Set `combinator` explicitly.
- The templates contain no credentials. Never enter secrets in nodes; use credentials or environment variables.

## License

MIT, see `LICENSE`.
