# faahims.wiki

A sourced reference work on the **Human Intervention Motivation Study (HIMS)**, the
Federal Aviation Administration programme that governs identification, treatment,
monitoring and return-to-duty for aviation professionals with substance use disorders.

**Live site: [faahims.wiki](https://faahims.wiki/)**

The site is a single static article backed by a searchable archive of the primary
sources it cites. No trackers, no analytics, no third-party requests, no build step.

---

## What is here

| | |
|---|---|
| `index.html` | The article. 165 cited references, full-text search, table of contents. |
| `documents.html` | Index to the document archive, grouped by provenance. |
| `docs/paf/` | 80 primary source documents, 1,132 pages, all with extractable text. |
| `search-index.json` | Page-level full-text index of every document, built from the PDFs. |
| `sitemap-index.xml` | Sitemap index; children are `sitemap.xml` and `sitemap-documents.xml`. |
| `llms.txt` | Structured summary for language models, per the llms.txt convention. |
| `robots.txt` | Open to all crawlers, including AI and archival agents. |

## The document archive

Eighty documents, every page searchable from the article itself. The archive draws on
four sources:

- **The FAA's Other Transaction Agreement with the Air Line Pilots Association**
  (693KA9-20-H-00004, 22 September 2020, $530,632.07) — the agreement in force during
  the congressionally mandated National Academies study. Its scanned pages were put
  through optical character recognition, so the statement of work is searchable.
- **The National Academies public access file** for project DBASSE-BBCSS-22-01,
  released by the Public Access Records Office in August 2026.
- **The FAA Guide for Aviation Medical Examiners** — the certification and monitoring
  instruments HIMS AMEs work from, including four successive versions of the Step Down
  Plan.
- **Federal audit, court and rulemaking records**, and the operational documents the
  programme publishes itself.

Journal articles under publisher copyright are cited rather than hosted.

## Search

Two independent search modes, both client-side:

- **Find in this article** — jumps between matches in the page text.
- **Search the source documents** — queries the full text of all 80 documents and links
  to the exact page, carrying the query into the PDF viewer where the viewer supports it.

The document index is fetched only on first use.

## Building and editing

There is no build step. The site is hand-authored HTML with inline CSS and JavaScript,
served directly by GitHub Pages. Editing `index.html` in the browser is a supported
workflow, which is why the code avoids anything requiring recompilation.

When adding documents to `docs/paf/`, `search-index.json` and `sitemap-documents.xml`
must be regenerated together — the archive page, the index and the sitemap are checked
against each other and must list exactly the same files.

## Corrections

Factual corrections are welcome and acted on. Open an issue, or write to the address in
[`.well-known/security.txt`](.well-known/security.txt).

Every quotation in the article is checked against the source document it cites, and
where that document is in the archive, readers can verify it without leaving the site.

## Licence

Page content is available under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

United States government works and programme records reproduced in `docs/paf/` are
public records and carry their own status. Journal articles remain the copyright of
their publishers and are listed rather than reproduced.

## Not affiliated

FAAHIMS.wiki is not affiliated with the Federal Aviation Administration, the Air Line
Pilots Association, or himsprogram.com.
