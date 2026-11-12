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

1. Cut a branch from the default branch. Name it as the repository's guide says. Where the guide
   says nothing, name it after the issue it serves, for example
   `<your-name>/<issue-id>-short-description`.
2. Open a pull request. Say what changed, how you verified it, and what you found but did not fix.
3. Wait for CI to pass. Where the repository runs an automated review or a verifier agent, read
   what it found and fix what applies. A review from another person is welcome. A repository can
   require one for some paths (its `CODEOWNERS`) or branches; its own guide says which.
4. A person decides to merge, unless the repository's own guide lets an agent merge (see "Using
   an AI agent"). A change that a user cannot get back, and a change that weakens the
   repository's checks, always needs a person to look at it first.
5. Merge by squash. The branch is deleted after the merge.

## Using an AI agent

GitHub cannot tell an agent from the person whose account it uses: an agent can do whatever that
account can do. These rules are for the person who runs the agent.

- An agent works under your account. Every commit, push, comment and pull request it makes is
  yours, and you answer for it.
- An agent can write code, run checks, push a branch, open a pull request, and delete a branch it
  created.
- A person, not an agent, approves a pull request, pushes or deletes a tag, uses a bypass,
  deletes a branch or repository the agent did not create, and changes organization or
  repository settings. A person also decides each merge, unless the rule after the next one
  applies.
- An agent can carry out a merge you decided, when you tell it in that session which pull request
  to merge at which head commit. A new head needs a new decision.
- A repository's own guide can let an agent merge without that decision. The guide must then name
  three things: the checks that must be green, the class of change that an agent does not merge
  by itself, and the place where each merge is announced. That class always includes a change
  that a user cannot get back (stored user data deleted or migrated, user data that leaves the
  device, an updater or an over-the-air release, an action taken for the user that cannot be
  undone) and a change that weakens the repository's checks. For that class a person looks at
  the change first, and the pull request records who looked and when. A person can stop any
  agent merge, in the way the guide names.
- In both cases the agent waits until every required check is in, then runs
  `gh pr merge <number> --squash --match-head-commit <sha>`: GitHub merges only if the head is
  still that commit at the moment of the merge. An agent never uses `--auto`, never merges
  without `--match-head-commit`, and never merges by a bypass.
- Keep your own instructions and notes for an agent outside the checkout, for example in
  `~/.claude/CLAUDE.md` or `~/.codex/AGENTS.md`. A file in the checkout that only you use must be
  ignored by git. A repository's `AGENTS.md`, `CLAUDE.md` and `CONTRIBUTING.md` are rules for
  everyone; change them only through a pull request, under that repository's review rules.
- At the start of every session, before its first edit, an agent reads these rules and the
  repository's own guide. A repository whose guide does not point here needs the person to supply
  them. Before it pushes, it follows that guide: the branch name, the local checks, the pull
  request body.
- An agent does not put a password, key or token in a commit, a pull request, an issue or a log.

## Language

English is the official language. Text in any other language is a translation of the English
text. Write Slack messages (direct messages included), documents and Linear tickets in ASD-STE100
Simplified Technical English.

## Who to ask

- CI/CD and deploys: send a direct message to Chaolei Pan.
- Account permission, finance or HR: send a direct message to Ray Zhang.
- Any other question: ask Samuel Chang, and wait for him to send you to the right person.

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
