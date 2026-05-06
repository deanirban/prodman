# Requirements

Product management artifacts for HPE GreenLake Platform capabilities and service-intake namespaces.

- `capabilities/` � cross-cutting platform capabilities (each maps to an Aha workspace)
- `services-intake/` � service-specific onboarding and intake artifacts

## How epics are created in Aha

Drop a markdown file with an `# H1 heading` into any `epics/` subfolder and merge the PR to `main`.
The `sync-aha-epics` GitHub Actions workflow will automatically create the corresponding epic in the mapped Aha workspace.

## PRD templates

Use the shared PRD templates below when creating documents in any `prds/` folder:

- Capabilities PRD template: `.github/PRD_TEMPLATE_CAPABILITIES.md`
- Service-intake PRD template: `.github/PRD_TEMPLATE_SERVICE.md`

Template sources in Aha:

- Capabilities: https://hpepm.aha.io/pages/GLCP2-N-33
- Service: https://hpepm.aha.io/pages/GLCP16-N-17

## How PRDs are synced to Aha

When a PR that changes files under `requirements/*/*/prds/*.md` is merged to `main`,
the `.github/workflows/sync-aha-prds.yml` workflow creates an Aha note in the
mapped workspace.

Parent page resolution order per workspace:

1. Explicit override in workflow map (example: GLCP17 -> GLCP17-N-4)
2. `<workspace>-N-4`
3. `<workspace>-N-3`

If no parent page is found, the note is created as top-level in that workspace
and the workflow logs a warning.
