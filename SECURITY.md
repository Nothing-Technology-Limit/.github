# Security

## Report a problem

Do not open a public issue, pull request or discussion about a security problem.

- **Members of this organization:** tell an organization owner directly, in a private message.
- **Anyone else:** follow Nothing's [vulnerability report page](https://nothing.tech/pages/vulnerability-report).

Say what you found, where, and how to reproduce it. Do not include the secret itself.

## A secret was committed

1. **Revoke or rotate it first.** A secret in git history is exposed even after the file is deleted,
   and every clone and fork already has it.
2. Tell an organization owner.
3. Then remove it from the repository.
