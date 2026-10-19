# Contributing

These rules apply to every repository in this organization. A repository can add rules of its own
in its `CONTRIBUTING.md`, `AGENTS.md` or `CLAUDE.md`; where they are stricter, they win.

## The baseline

**Everyone follows these:**

- Turn on two-factor authentication. Without it, a member keeps the membership but cannot open the
  organization's repositories, and an outside collaborator is removed.
- Change a repository through a branch and a pull request. Do not push to the default branch
  directly, and do not force-push a branch that someone else uses.
- Merge by squash, and delete the branch after the merge.
- Ask an organization owner for a new repository. Every repository records an owner and a backup,
  who answer for it.

**GitHub enforces these in every active development repository:**

- A member can read every repository. Write access comes from a team or from a grant on the
  repository.
- The default branch cannot be deleted or force-pushed. Organization owners can bypass this, and
  GitHub records each bypass.
- A pull request can merge only by squash, and GitHub deletes its branch after the merge, unless
  that branch is itself protected.
- Only organization owners create, delete, transfer or change the visibility of a repository.
  Private repositories cannot be forked.

Designated mirrors follow their own documented synchronization policy. Archived repositories are
read-only.

## What a repository can add

A repository can protect more: a pull request for every change, required checks, a review from a
code owner for some paths, protected release branches, protected tags. Its own guide says which.
Read it before your first change. When a rule here and a rule there disagree, the stricter one wins.

## How a change reaches a repository

1. Cut a short-lived branch from the default branch. Name it after the issue it serves, for example
   `<your-name>/<issue-id>-short-description`.
2. Open a pull request. Say what changed, how you verified it, and what you found but did not fix.
3. Wait for CI to pass. Where the repository runs an automated review, it comments on the pull
   request; read what it found and fix what applies. A review from another person is welcome, and a repository can require one for
   some paths (its `CODEOWNERS`) or branches (release branches need one approval).
4. A person decides to merge. An AI agent can prepare a change, and can carry out a merge a person
   decided (see "Using an AI agent"); it never decides one.
5. Merge by squash. The branch is deleted after the merge.

## Using an AI agent

GitHub cannot tell an agent from the person whose account it uses: an agent can do whatever that
account can do. These rules are for the person who runs the agent.

- An agent works under your account. Every commit, push, comment and pull request it makes is
  yours, and you answer for it.
- An agent can write code, run checks, push a branch, open a pull request, and delete a branch it
  created.
- A person, not an agent, approves a pull request, decides to merge one, pushes or deletes a tag,
  uses a bypass, deletes a branch or repository the agent did not create, and changes organization
  or repository settings.
- An agent can carry out a merge you decided, when you tell it in that session which pull request
  to merge at which head commit. It waits until every required check and approval is in, then runs
  `gh pr merge <number> --squash --match-head-commit <sha>` with that commit: GitHub merges only if
  the head is still that commit at the moment of the merge, and a new head needs a new decision.
  An agent never uses `--auto`, never merges on its own reading of a pull request, never without
  `--match-head-commit`, and never by a bypass.
- Keep your own instructions and notes for an agent outside the checkout, for example in
  `~/.claude/CLAUDE.md` or `~/.codex/AGENTS.md`. A file in the checkout that only you use must be
  ignored by git. A repository's `AGENTS.md`, `CLAUDE.md` and `CONTRIBUTING.md` are rules for
  everyone; change them only through a pull request, under that repository's review rules.
- At the start of every session, before its first edit, an agent reads these rules and the
  repository's own guide. A repository whose guide does not point here needs the person to supply
  them. Before it pushes, it follows that guide: the branch name, the local checks, the pull
  request body.
- An agent does not put a password, key or token in a commit, a pull request, an issue or a log.

## Outside collaborators

An outside collaborator gets access to named repositories, not through a team. Ask the repository's
owner for access, follow that repository's guide, and turn on two-factor authentication before you
start. When your work ends, tell the owner, so the access is removed.

## Forks

Private repositories here cannot be forked. If you have write access, push a branch to the
repository itself.

## Never commit

Passwords, API keys, tokens or private keys; personal or user data; raw recordings or transcripts;
production logs; binaries you can build from source. If a secret reaches git history, revoke or
rotate it first (see `SECURITY.md`). Deleting the file does not remove it from history.
