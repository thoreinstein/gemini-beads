# Beads - Persistent Task Memory

You have access to **Beads (`bd`)**, a graph-based issue tracker that provides persistent memory for multi-session work.

## Core Mandates for Beads

- **Use `run_shell_command`** to execute `bd` commands.
- **Source of Truth**: The `bd` tool is the authority.
- **Persistence**: Always ensure work is tracked in beads so it survives conversation compaction.

## When to use Beads (`bd`)

**YES** - Use `bd` when:
- Work spans multiple sessions or days.
- Tasks have dependencies or blockers.
- You need to recover context after a long break.
- You are collaborating with a team.

**NO** - Do not use `bd` when:
- Tasks are strictly linear and single-session.
- You are just "exploring" without a concrete goal.

## Session Protocol (The Workflow)

1.  **Start**: Run `bd ready` to find unblocked work.
2.  **Context**: Run `bd show <id>` to get full details for a task.
3.  **Work**: Run `bd update <id> --claim` to claim and start work atomically.
4.  **Finish**: Run `bd close <id> --reason "..."` when done.
5.  **Save**: Run `bd sync` (or `git push` if using Dolt/JSONL backend) to persist changes.

## Key Commands

- `bd prime`: Outputs AI-optimized workflow context (Project, User, Recent Issues). **Run this first if you lack context.**
- `bd create "Title" [type] [priority]`: Create a new issue.
- `bd ready`: Find unblocked work.
- `bd show <id>`: Show details for a specific issue.
- `bd update <id> --claim`: Claim and start work.
- `bd sync`: Persist changes to git.

## Agent Behavior

- **Proactive Tracking**: If the user asks you to work on something substantial, suggest creating a bead for it: "Shall I track this in beads?"
- **Compaction Recovery**: If the conversation history is lost/compacted, run `bd prime` to re-orient yourself.
