# Handoff: From God's Law to the Law of Utility (slug `man-made-law`)

Arabic / English reading site for Thaer Salameh's *من شريعة الله إلى شريعة
المصلحة: جذور الإسلام الليبرالي المحدث ودوره في إنتاج «فقه الأقليات»*, built
with the new-book-engine (`~/Sites/new-book-engine`; read its `CLAUDE.md` and
the first section of `docs/LEARNINGS.md` first).

## State (5 Oct 2026)

- 201 pages in both languages, `check_site.py`: 0 failures, 2 warnings (verse
  brackets in the engine's English use plain quotes in places; Latin acronyms
  and pasted URLs in the Arabic, see below). Live at
  https://nisbeti.github.io/aqeedah/man-made-law/ once pushed.
- **Not published**: no git repo, no GitHub repo, no domain (`domain` is
  `null`). Ask the owner before each.
- `book.json` summaries are drafts from the Arabic executive summary.
- Dev preview: engine `.claude/launch.json` entry `man-made-law`, port 8769.

## Arabic

Source: `.docx` + PDF from an archive.org download
(`20250818_20250818_0145`). Pages come from the PDF via the OCR
(`split_docx_pages.py --ocr <_djvu.xml>`); page N is PDF page N, so the book's
printed contents numbers are already right (`index.refs_fixed` true; entries on
pages 5-8 rewritten as `title ... N`).

Done by hand: page 1 (cover picture: title, subtitle, author typed), page 2 is a
blank PDF page (kept as "(صفحة بيضاء)" so numbering matches), word orphans left
at a page end moved (23, 93), a table row moved (105 to 106), the heading
"عن المؤلف" moved to the top of 199. Table pages were checked against the PDF
images (73, 103-106, 128, 132, 134). Pages 36/40-style flowchart pictures, if any,
are not in the text. Source quirks left alone: footnote numbers are not in order
on some pages (the docx's own numbering), and notes began with an empty `()`
which was removed. Five runs of spaces that were arrows became "←".
`find_garbled.py` reports 91 runs: all Latin acronyms and pasted citation junk
(`aljazeera.net`, `shamela.ws`), none Qur'anic. Left as in the source.

## English: where it comes from

The supplied English (nested folder) is not a parallel text: 2,911 paragraphs
to the Arabic's 2,254, shorter overall, with an added summary and author blurb,
and only 2 notes against 51. `align_english.py` fitted it, but reading the fitted
pages against the Arabic showed it was out of step page after page, so **every
page from 3 to 201 was translated by the engine** (gpt-4o-mini Batch API, in
passes, as pages failed or looked shifted). Pages 1 and 2 (cover, blank page) are
typed; pages 65 and 81 were written by hand because the model kept merging their
lines (lettered lists) and mistranslated *al-mursal* as a hadith term.

Hand corrections on engine pages: verse references the model marked
`[illegible]` or dropped, the footnote marker on 42, "Geodance" to Guidance
Residential.

Backups in the engine's `work/`: `man-made-law-en-supplied` (fitted supplied
English), `man-made-law-en-before-part3` and `-before-part5` (en/ before the
later passes), `man-made-law-part*` (raw engine output). To redo a page: use a
scratch folder with just those `ar/N.txt` and run
`python3 scripts/translate_book_pages.py <folder>`, then copy the result in.

## Still open

- Engine pages were spot-read (pages 16, 20, 98, 141 and others), not read word by word.
- Owner to approve the `book.json` summaries.
- Publish when asked (engine `docs/DEPLOY.md`; keep `source/` out of the repo).
