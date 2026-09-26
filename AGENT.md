# Git workflow preference

The user wants Codex to handle Git synchronization, pull requests, and merges as part of requested repository work. Do not leave routine Git steps for the user to perform.

- Inspect the working tree and remotes before changing Git state. Preserve unrelated or pre-existing user changes, and commit only work related to the current task.
- Fetch and synchronize with the appropriate remote when needed. Push completed work to the intended remote as part of the task.
- When the user requests a pull request, prepare and create or update it, then attach it to the task. When the user requests a merge, complete the merge and sync the resulting branch if repository checks and protections allow.
- Never force-push, bypass branch protections or required checks, or merge a change that has not met its required gates. If a required external approval or an unresolved choice blocks completion, finish all work that can be done safely and ask only for that blocker.
