# Oxford Editorial Indexer

**A Claude Skill for glossary creation, project indexing, terminology control, and cross-reference discipline in UK English.**

*Author: TABARC-Code*

---

There is a particular kind of document chaos that only reveals itself slowly. A rulebook that calls the same component three different names across twelve chapters. A fiction bible where the ancient faction picks up a capital letter halfway through and nobody notices until the layout is done. An article series where a technical term quietly acquires a second meaning in part four and nobody goes back to fix parts one through three. This skill exists to stop that from happening — or, more honestly, to surface it before it becomes expensive.

The Oxford Editorial Indexer makes Claude behave like a disciplined publishing editor when working on large or complex projects. It extracts terms, defines them, builds project indexes, records and verifies cross-references, flags broken links, and maintains a style decision log. It works on UK English by default, enforces Oxford-style editorial habits, and knows the difference between an author's deliberate eccentricity and an accidental mess. It flags both. It only proposes to fix the second.

---

## What it does

Given a document or project, the skill produces up to eight editorial outputs in sequence:

1. **Editorial summary** — project type, reference unit, major structural issues, citation style
2. **Glossary** — controlled definitions with status, variants, and evidence
3. **Project index** — navigation-grade retrieval tool with see and see also cross-references
4. **Cross-reference register** — maintained bidirectional relationship records
5. **Style and terminology decision log** — explicit house style decisions
6. **Conflict list** — contradictions, duplicates, and capitalisation drift
7. **Missing definitions** — undefined terms that need author decisions
8. **Recommended next edits** — prioritised remaining work

Every output ends with a completion statement. A document that stops without one may have been truncated.

---

## What it works on

The skill handles most document types where consistent terminology matters:

- Rulebooks and game manuals (wargames, board games, RPGs, card games)
- Fiction bibles and worldbuilding documents
- Academic essays and research dossiers
- Article series and content libraries
- Brand systems and website content
- Technical manuals and product documentation
- RPG setting documents and campaign bibles
- Long documents that keep mutating in the dark like damp paperwork with ambitions

---

## Architecture

The skill is structured as a core SKILL.md with three sub-skills and four reference modules. They are not optional decoration. They are the working parts.

```text
oxford-editorial-indexer/
├── SKILL.md                              Core skill — load first
├── README.md
├── subskills/
│   ├── grammar-rules/
│   │   └── SKILL.md                     UK English grammar enforcement
│   ├── publishing-doctrine/
│   │   └── SKILL.md                     Document structure, citation, footnotes, TOC
│   └── writing-etiquette/
│       └── SKILL.md                     Tone, flagging language, author relationships
├── references/
│   ├── editorial-doctrine.md            Working identity, project-type handling
│   ├── glossary-schema.md               Glossary field definitions and rules
│   ├── indexing-schema.md               Index schema, sorting, orphan handling
│   └── cross-reference-discipline.md    Cross-ref types, bidirectional verification
├── templates/
│   ├── glossary-entry-template.md
│   ├── project-index-template.md
│   └── cross-reference-register-template.md
├── examples/
│   └── example-output.md
└── scripts/
    └── validate_registers.py            Register fault detection (Python 3.8+)
```

### Sub-skills

**grammar-rules** — governs sentence construction, punctuation, Oxford comma enforcement, capitalisation, number style, and register-appropriate grammar for glossary definitions, index notes, and cross-reference reason fields. Loaded for every output.

**publishing-doctrine** — governs document structure, heading hierarchy, citation style handling, footnote and endnote procedure, appendix control, table-of-contents guidance, versioning, and completeness statements. Loaded for formal document outputs.

**writing-etiquette** — governs tone for conflict notices, author-decision flags, style drift descriptions, and all explanatory editorial prose. Prevents complaint-framing. Enforces evidence-based, specific, professional language.

---

## Installation

Copy the folder to one of these locations:

```text
~/.claude/skills/oxford-editorial-indexer/
```

or inside a Claude project:

```text
.claude/skills/oxford-editorial-indexer/
```

Then invoke naturally:

```text
Please use the oxford-editorial-indexer skill on this document.
```

or by path if you prefer explicit invocation.

---

## Validation script

`scripts/validate_registers.py` checks Markdown or CSV register exports for:

- duplicate canonical terms
- `see` targets that do not exist as main headings
- cross-reference rows missing required reverse links
- orphaned cross-reference targets
- circular references with no independent definition
- empty definition or reason fields
- unusual or missing status values
- per-register statistics summary

Requires Python 3.8 or later. No dependencies beyond the standard library.

```bash
python3 scripts/validate_registers.py glossary.md index.md crossrefs.md
```

Exit codes: `0` clean, `1` faults found, `2` file not found.

---

## Cross-skill integrations

This skill is designed to work alongside other Claude Skills, not in isolation. The most useful combinations:

| Companion skill | Combined use |
|---|---|
| `professional-technical-writing` | Rulebooks and manuals — that skill writes, this skill organises |
| `wargame-designer` | Wargame and miniatures rulebooks — design companion |
| `forensic-style-auditor` | Run before indexing to identify the author's voice signature |
| `speculative-fiction-writer` | Fiction bible companion |
| `web-seo-master` | Website and brand content — that skill optimises, this skill keeps terminology consistent |
| `humanizer` | Apply to editorial summaries before publication |
| `kaizen` | Apply to register maintenance — small, verifiable corrections with a traceable history |

---

## Notes

This is an editorial discipline skill. It is not an official Oxford University Press product. `Oxford-style` is used to mean the practical editorial habits of careful, consistent, evidence-based document management — not a licensed affiliation.

It will not rewrite your prose. It will not smooth out your author's eccentricities. It will not pretend your contradictions are consistency. It will tell you what it found, frame it precisely, and leave the decisions to you.

That is the arrangement.

---

*Author: TABARC-Code*
*Skill version: 2.0.0*
