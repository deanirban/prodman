# Requirements

Product management artifacts for HPE GreenLake Platform capabilities and service-intake namespaces.

- `capabilities/` — cross-cutting platform capabilities (each maps to an Aha workspace)
- `services-intake/` — service-specific onboarding and intake artifacts

## How epics are created in Aha

Drop a markdown file with an `# H1 heading` into any `epics/` subfolder and merge the PR to `main`.
The `sync-aha-epics` GitHub Actions workflow will automatically create the corresponding epic in the mapped Aha workspace.
