# Security and privacy

This is a static creative-coding demonstration, not a service, application backend, or security product.

## Runtime considerations

- The animation loads GSAP from a public CDN; an internet connection and trust in that third-party delivery path are required unless the dependency is vendored separately with appropriate permission.
- The development tooling (`npx` and HyperFrames) executes third-party packages locally. Inspect versions and dependencies before running them.
- The project does not require API keys, user accounts, or local network access to function. Do not add secrets to the source or repository.

## Reporting

For security issues, avoid posting tokens, credentials, or personally identifiable information in a public GitHub issue. Use a private reporting channel if one is enabled on the repository.

## Before making the repository public

Review the entire **staged diff** and Git author metadata. Do not commit local cache directories, generated diagnostic reports, filesystem paths, environment files, or screenshots containing application chrome. See [publish checklist](docs/PUBLISH_CHECKLIST.md).
