# Security policy

Please don't report a security problem in a public issue or discussion.

## How to report

Open a
[private vulnerability report](https://github.com/consealdev/conseal/security/advisories/new)
on consealdev/conseal. Only Codesense can see it. Use it for a problem in any
conseal repository. If you're unsure whether something qualifies, report it
privately anyway.

Include what you can of:

- the package and its version: `@consealdev/conseal`, and which entry point, or
  `ConsealDev.Conseal`
- what an attacker could do, and what they would need first: control of the
  server, a script in the app's page, a stolen device, or something else
- the smallest code that shows it

## After you report

- We acknowledge a report within 7 days.
- Within 30 days we tell you what we found: when a fix ships, or why the report
  is out of scope.
- Nothing is disclosed before a fix ships, unless we agree otherwise with you.
- With your permission, we credit you in the release notes.

## What's covered

- `@consealdev/conseal`: the core (sealing, key wrapping, the circle and
  channels), sync (`CircleClient` and the join ceremony, `SyncEngine`, records,
  blobs, export and backup, the identity) and the components (the ceremony
  screens)
- `ConsealDev.Conseal`, the .NET backend
- The spec, where a backend that follows it would be open to an attack

A report is in scope when it breaks something the
[threat model](https://github.com/consealdev/conseal/blob/main/threat-model.md)
says conseal enforces. For example:

- a server or a network attacker that can read data or keys, or test
  passphrase guesses, where the threat model says it can't
- ciphertext, a record or a blob that still opens after tampering, or opens in
  a place other than its own
- a join that gives the account key to a device the user didn't approve, though
  the user compared the codes
- a key reachable from JavaScript that conseal holds as non-extractable
- weak randomness, such as a recovery phrase with too little entropy, or
  PBKDF2, salt or IV handling below what the threat model documents
- the backend breaking a rule the spec says it enforces, or letting one user
  read or change another user's data

## Out of scope

What the threat model lists as relied on, or not protected against:

- a script running in the app's origin, including XSS (§11.1)
- a compromised server that serves the app's own code (§11.2)
- side channels against the browser's crypto (§11.3), and key bytes in
  JavaScript memory (§11.4)
- weak passphrases (§11.5), and losing or exposing the Secret Key or the
  recovery phrase (§11.6, §11.7)
- what the server learns about who syncs what, and when (§10)
- an app that breaks a caller assumption (§12), such as approving a join
  without the user comparing the codes
- features not yet built

## Supported versions

conseal is before 1.0. Fixes ship in a new release of the latest minor version.
Older versions are not patched, so upgrade to get a fix.

## Bug bounty

There is no bounty programme yet. Valid reports are credited in the release
notes. A formal programme is planned before or at 1.0.

Reports are read in English.
