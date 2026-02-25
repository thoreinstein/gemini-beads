# Release Notes - v0.3.0

## Summary
This release marks a significant architectural shift to the Dolt-based storage backend, providing improved data integrity and synchronization capabilities for the Gemini Beads extension.

## New Features
- **Decision Tracking**: Introduced the `bd decision` command to capture and track architectural and project decisions directly within the beads issue graph.
- **Enhanced AI Command Definitions**: Refined the TOML command definitions for `create`, `sync`, and `update` to provide better guidance to the AI agent during tool calling.

## Bug Fixes
- **Dependency Direction Corrected**: Documentation and tool prompts now correctly emphasize the "from_id depends on to_id" relationship (`bd dep add <blocked> <prerequisite>`).
- **Trailing Whitespace Removal**: Cleaned up internal command definitions.

## Operational Notes
- **Performance Optimization**: Refactored the `SessionStart` and `PreCompress` hooks to use concise `bd prime` output, reducing token consumption and improving startup latency.
- **Workflow Update**: The standard workflow now recommends the atomic `--claim` flag for starting work on an issue to prevent race conditions.
- **Minimum `bd` CLI Version**: Recommended version updated to `0.53.0`.

## Commit History (v0.2.0..v0.3.0)
- f86b617: refactor(hooks): simplify bd prime hook output
- b6058fe: feat(beads): update command definitions and add decision command
- 429aaba: docs(beads): align documentation with Dolt-based architecture and claim workflow
