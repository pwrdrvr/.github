# Security Policy

This policy covers every public repository under
[github.com/pwrdrvr](https://github.com/pwrdrvr) that does not define its own —
GitHub inherits this file across the organization.

## Reporting a vulnerability

Email **security@pwrdrvr.com**.

Please include enough to reproduce it: the product and version, the platform,
what you did, and what happened. A proof of concept helps but is not required to
start the conversation.

**Do not open a public issue for a security problem.** Use the email address
above, or GitHub's [private vulnerability
reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
on the affected repository, which routes to the same person.

Machine-readable contact details, per RFC 9116:
<https://pwrdrvr.com/.well-known/security.txt>

## What to expect

PwrDrvr LLC is a small company. You will get a real reply from a real person
rather than a ticket number, but not instantly.

- **Acknowledgement** within 3 business days.
- **An assessment** — whether it reproduces, and how we rate it — within 10
  business days.
- **A fix or a plan**, with a target date, once the assessment is done.
- **Credit** in the release notes if you want it, and none if you would rather
  stay anonymous. Say which.

If you have not heard back in 5 business days, assume the mail went astray and
follow up through [linkedin.com/company/pwrdrvr](https://www.linkedin.com/company/pwrdrvr/).

## Scope

In scope: the desktop applications and their release artifacts
([PwrAgent](https://github.com/pwrdrvr/PwrAgent),
[PwrSnap](https://github.com/pwrdrvr/PwrSnap), PwrGit), the libraries published
under this organization, and the websites at pwrdrvr.com, pwragent.ai, and
pwrsnap.com.

Particularly interesting, because of what these applications do:

- Anything that lets a remote party reach the local agent or the local file
  system without the operator approving it.
- Credential handling — bot tokens, agent sign-in state, and anything that
  writes them somewhere they should not be.
- Weaknesses in signing, notarization, or update verification.
- Redaction that fails to redact, in PwrSnap's blur and annotation paths.

Out of scope: findings against third-party services these products connect to
(report those to the service), and reports generated purely by an automated
scanner with no demonstrated impact.

## Disclosure

We will work with you on a disclosure timeline. Our default is to publish an
advisory once a fix has shipped, and we would rather that happen sooner than
later. If a fix is taking longer than it should, tell us — we would rather hear
that from you than read it somewhere else.

## Signing

All release artifacts are signed under PwrDrvr LLC, and a signature that does
not verify is itself worth reporting.

- **macOS** — Developer ID-signed and Apple-notarized. Verify with
  `spctl -a -vvv -t install /Applications/<App>.app`.
- **Windows** — signed through Azure Trusted Signing, installers and the
  executables inside them. Verify with
  `Get-AuthenticodeSignature .\<installer>.exe | Format-List`.

We publish downloads only through GitHub Releases and our
[Homebrew tap](https://github.com/pwrdrvr/homebrew-tap). We have never asked
anyone to disable a security control to install our software; a download that
does is not ours.
