# Contributing

These rules apply to every repository in this organization. A repository can add rules of its own
in its `CONTRIBUTING.md`, `AGENTS.md` or `CLAUDE.md`; where they are stricter, they win.

## How a change reaches a repository

1. Cut a short-lived branch from the default branch. Name it after the issue it serves, for example
   `<your-name>/<issue-id>-short-description`.
2. Open a pull request. Say what changed, how you verified it, and what you found but did not fix.
3. Wait for CI to pass. Where the repository runs an automated review, it comments on the pull
   request; read what it found and fix what applies. A review from another person is welcome, and a repository can require one for
   some paths (its `CODEOWNERS`) or branches (release branches need one approval).
4. A person decides to merge. AI agents can prepare a change, but they do not merge it.
5. Merge by squash. The branch is deleted after the merge.

Do not push to the default branch directly, and do not force-push a branch that someone else uses.

## Forks

Private repositories here cannot be forked. If you have write access, push a branch to the
repository itself.

## Never commit

Passwords, API keys, tokens or private keys; personal or user data; raw recordings or transcripts;
production logs; binaries you can build from source. If a secret reaches git history, revoke or
rotate it first (see `SECURITY.md`). Deleting the file does not remove it from history.

## A new repository

Members ask an organization owner. Only owners create, delete, transfer or change the visibility
of a repository.
