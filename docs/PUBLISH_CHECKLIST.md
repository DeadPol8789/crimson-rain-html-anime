# Private publication checklist (keep this file public only if all items are generic)

This checklist is generic. It must never contain audit matches, private paths, secrets, or screenshots of private tooling.

## Prepare isolated repository

- [ ] Create a **new** empty local directory, not a fork or copy of the entire upstream Git repository.
- [ ] Copy only the final film's `index.html` from the local prototype.
- [ ] Copy these documentation files and the cropped `assets/preview.png`.
- [ ] Optionally render and review `assets/demo.mp4`; omit it if unverified, oversized, or containing metadata not intended for publication.
- [ ] Verify the source is original/adapted only under the applicable open-source terms; retain attribution and upstream copyright notices.

## Privacy and security

- [ ] Check `index.html`, README, docs, SVG metadata, image metadata, and video metadata.
- [ ] Search for local Windows paths, usernames, home directories, email addresses, personal names, local/private IPs, hostnames, domain names, API tokens, cookies, authorization headers, keys, internal service names and network topology.
- [ ] Confirm no private log, diagnostic file, `.hyperframes` artifacts, caches, credentials, backups, or unrelated project files are staged.
- [ ] Confirm `.gitignore` is present but **do not rely on it as a security scan**.
- [ ] Ensure the local Git commit author email uses an intentionally public address or GitHub-provided `noreply` address. Do not invent a `noreply` value.
- [ ] Confirm only new, intentionally public Git history will be pushed; never copy the upstream `.git` directory.
- [ ] Verify the screenshot shows **only** the rendered art and has no embedded private metadata.

## Verification and publication

- [ ] Run the pinned `lint` and `check` commands from the standalone project root.
- [ ] Review output warnings instead of claiming that there are none.
- [ ] Preview the result manually; if rendering MP4, inspect it in a video player.
- [ ] Stage **explicit named paths** rather than `git add .`.
- [ ] Inspect `git status --short`, `git diff --cached --stat`, and the complete `git diff --cached` before the initial commit.
- [ ] Confirm no email or hostname is exposed in the commit author/committer metadata.
- [ ] Only create a remote public repository and push after the user explicitly approves publication.

If a secret is discovered **after** publication, revoke or rotate it promptly. Deleting the current file does not remove it from Git history.
