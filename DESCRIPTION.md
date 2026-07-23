# Oxford Editorial Indexer — Repository Description

*Author: TABARC-Code*

---

A Claude Skill that applies Oxford-style editorial discipline to UK English documents. Produces controlled glossaries, project indexes, bidirectional cross-reference registers, and style decision logs for rulebooks, fiction bibles, technical manuals, article series, and brand systems.

Includes three sub-skills (grammar enforcement, publishing doctrine, writing etiquette), four reference modules, three output templates, an example, and a Python validation script for register fault detection.

Designed for projects where terminology, naming, and internal consistency are not optional.

---

## Extended description

Most long documents have a consistency problem they are not aware of. The rulebook that spells the keyword two ways. The worldbuilding document where the empire picks up a definite article halfway through and keeps it. The article series where a technical term drifts. These are not dramatic failures. They accumulate quietly, and they become expensive when the document needs a second person — an editor, a designer, a translator, a future author building on top of the existing work.

The Oxford Editorial Indexer is a Claude Skill that addresses this. When active, it operates as a disciplined UK English project editor. It reads the source, extracts the vocabulary, builds a controlled glossary, creates a navigation-grade project index, records and verifies cross-references, and produces a conflict list for everything it cannot resolve without the author's input.

The skill does not rewrite. It does not impose. It maps. Everything it flags is flagged with evidence and a recommended resolution framed as a recommendation rather than a correction. What the author does with that information is entirely the author's business.

The architecture is modular. Three sub-skills handle grammar enforcement, publishing-house document structure, and editorial tone respectively. Four reference modules provide detailed schemas for glossaries, indexes, and cross-references, and the editorial doctrine governing how different project types are handled. Templates and an example output provide a practical starting point. A Python script validates finished registers for broken links, missing reverse links, orphaned entries, and circular references.

The validator is worth running. It finds things that look fine on a casual read. That is the point of automation in this context — not to replace editorial judgement, but to catch the errors that happen when a human has been staring at the same table for forty minutes and has stopped seeing the column that says `reverse link required: yes` and the column next to it that says `reverse link present: no`.

This is a skill for projects that take their documents seriously. It is not for everything. A short blog post does not need a cross-reference register. A 200-page rulebook probably does.

---

## Topics

`claude-skill` · `editorial` · `indexing` · `glossary` · `uk-english` · `cross-reference` · `terminology` · `publishing` · `rulebook` · `fiction-bible` · `technical-writing` · `document-management` · `tabarc-code`

---

## Repository metadata

| Field | Value |
|---|---|
| Language | Markdown, Python 3.8+ |
| Python dependencies | None (standard library only) |
| Skill version | 2.0.0 |
| UK English | Yes |
| Author | TABARC-Code |
| Licence | See repository |

---

*TABARC-Code builds Claude Skills for tabletop game design, editorial discipline, and structured content work.*
