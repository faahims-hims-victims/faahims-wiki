# Security policy

## Reporting

Email **FAAHIMSProgram@pm.me**, or use GitHub's
[private vulnerability reporting](https://github.com/faahims-hims-victims/faahims-wiki/security/advisories/new)
if you would rather keep it inside GitHub.

The same address is published at
[`/.well-known/security.txt`](https://faahims.wiki/.well-known/security.txt).

Please don't open a public issue for a security finding. Anything else — a
broken link, a formatting problem, a citation that doesn't check out — is
welcome as a public issue.

Expect a reply within a few days. This is a small project maintained by a very 
small (but dedicated!), number of people; not a staffed security team.

## What this project is

A static site on GitHub Pages. Hand-authored HTML with inline CSS and
JavaScript, no build step, no dependencies, no server-side code, no database,
no user accounts, no forms, and no data collected from visitors.

That removes most of the usual attack surface. What remains is worth being
precise about.

## Where the interesting surface is

**The client-side document search.** `index.html` fetches
`search-index.json` and builds result markup from it. Two untrusted-ish inputs
meet there: the visitor's query, and the contents of the index itself. Both are
escaped before reaching the DOM, filenames are validated against a strict
pattern, and page numbers are coerced to integers — but this is the part of the
code most worth reading if you are looking for a flaw.

**Anchor and fragment handling.** A delegated click handler intercepts in-page
links and scrolls manually. It decodes URL fragments defensively, and modifier
and non-primary clicks are passed through to the browser.

**The content security policy.** Delivered by meta tag, since GitHub Pages
cannot set headers. It permits `'unsafe-inline'` because the site's own script
and style are inline; hashing them would break the browser-based editing this
project depends on. The policy is therefore about containment rather than
prevention: an injected script cannot load external code, beacon data
off-domain, embed a frame or plugin, or inject a `<base>` tag.

Reports demonstrating a bypass of that containment, or any path from visitor
input to script execution, are exactly what this policy is for.

## Out of scope

**The hosted documents.** `docs/paf/` contains United States government works
and programme records — public records, published deliberately. They are not
assets to be protected, and their being readable is the point. Reports that the
PDFs are publicly accessible, enumerable, or listed in a sitemap are not
vulnerabilities.

**Missing HTTP security headers.** GitHub Pages does not allow custom response
headers. `X-Frame-Options`, `Strict-Transport-Security` on a custom domain, and
`X-Content-Type-Options` cannot be set from a repository. Reports of their
absence will be acknowledged but cannot be acted on.

**`'unsafe-inline'` in the content security policy.** Known, deliberate, and
explained above. A demonstrated exploit that the policy fails to contain is in
scope; the directive's presence by itself is not.

**Self-XSS.** Typing a payload into the site's own search box and observing it
in your own browser is not a finding. Show a path by which one visitor's input
reaches another visitor.

**Findings from automated scanners with no demonstrated impact.** Please read
the code before reporting.

**Third-party sites** this project links to, and the National Academies,
Federal Aviation Administration, and Air Line Pilots Association, none of whom
are affiliated with this project.

## Disclosure

Report privately first. Once a fix is deployed, publish whatever you like —
credit is given gladly and the commit history is public in any case.

There is no bounty. This is a public-interest reference work with no revenue.

## Corrections to content

Factual corrections are treated as seriously as security reports and are the
more likely reason to get in touch. Every quotation in the article is checked
against the source it cites, and where that source is in `docs/paf/`, you can
verify it without leaving the site. If something does not check out, say so and
include the section anchor and the source you believe is authoritative.
