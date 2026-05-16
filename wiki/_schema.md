---
tags:
  - schema
  - meta
---
# CPT304 Wiki Schema

This document defines the conventions and structure for the CPT304 course wiki. It serves as a guide for LLM agents maintaining this knowledge base.

## Directory Structure

```
wiki/
├── _schema.md          ← This file — wiki conventions and workflows
├── index.md            ← Master catalog of all wiki pages
├── log.md              ← Chronological activity log
├── *.md                ← Topic pages (one per major concept or module)
└── concepts/           ← Cross-cutting concept pages
    └── *.md
```

## File Conventions

### YAML Frontmatter

Every page **must** include frontmatter with:

```yaml
---
tags:
  - cpt304
  - <module-tag>
source: <source-lecture-number>
---
```

### Wiki-links

- Use `[[wiki/page-name]]` for internal wiki links
- Use `[[Clippings/lecture N]]` for source reference links
- Use `[[wiki/concepts/concept-name]]` for cross-cutting concept pages

### Page Structure

- Start with an `## Overview` section summarizing the topic
- Use `##` for major sections, `###` for subsections
- End with `## Related Pages` listing wiki-links to connected topics
- End with `## Sources` listing links to source lecture files

## Operations

### Ingest

When a new source is added to `Clippings/`:

1. Read the source file
2. Identify which existing wiki pages need updating
3. Update or create pages with new information
4. Update `index.md` if new pages are created
5. Append an entry to `log.md`

### Query

When answering questions:

1. Read `index.md` to find relevant pages
2. Read identified pages for detailed content
3. Synthesize answer with citations to wiki pages and source files
4. File valuable answers back into the wiki as new pages

### Lint

Periodically check for:

- Contradictions between pages
- Stale claims superseded by newer content
- Orphan pages with no inbound links
- Missing cross-references
- Important concepts mentioned but lacking their own page
