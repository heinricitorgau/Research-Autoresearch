# Security Policy

## Reporting a vulnerability

Please **do not open a public issue** for security problems.

Report them privately through GitHub's Private vulnerability reporting:

1. Go to the repository's **Security** tab.
2. Click **Report a vulnerability**.
3. Describe the problem, how to reproduce it, and its impact.

Direct link: <https://github.com/heinricitorgau/research-autoresearch/security/advisories/new>

You should get a first response within 7 days. Please give us a reasonable time to fix the issue before disclosing it publicly.

## Scope

Examples of things worth reporting:

- Code paths that download or execute untrusted content (for example in data preparation).
- Unsafe deserialization of checkpoints or cached files.
- Dependencies pinned to versions with known vulnerabilities.

## Supported versions

Only the latest commit on `main` is supported.
