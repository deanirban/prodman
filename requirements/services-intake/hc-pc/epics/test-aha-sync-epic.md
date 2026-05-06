# [Test] Aha GitHub Actions Sync Validation

## Summary

This is a test epic used to validate the GitHub Actions workflow that automatically
creates Aha epics in release **GLCP17-R-1** when a new `.md` file is merged into
`requirements/services-intake/hc-pc/epics/`.

## Acceptance Criteria

- A corresponding epic should appear in Aha release GLCP17-R-1 after this PR is merged.
- The epic name in Aha should match the H1 heading above.
- The epic description in Aha should contain this body content.

## Notes

- This file can be deleted once the workflow is confirmed working.
- Workflow source: `.github/workflows/sync-aha-epics.yml`
