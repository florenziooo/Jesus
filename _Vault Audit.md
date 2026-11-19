# Vault Audit

Record of the Scripture Reference build, inline backlinking, formatting pass, and
titling run on 2026-09-02.

> [!warning] Backup lives in temporary storage
> The pre-run vault is at
> `/private/tmp/claude-501/.../scratchpad/vault-backup-20260902-025608/`.
> That is scratch space and will not survive indefinitely — copy it somewhere
> permanent, or better, run `git init` in this vault so future passes are revertible.

## 1. Headline numbers

| | |
|---|---|
| Total notes | 162 |
| Your notes | 69 |
| Scripture Reference notes | 93 (49 OT / 44 NT) |
| NLT verses retrieved | 230 |
| Placeholders / unsourced verses | **0** |
| Inline scripture links | 150 |
| Quote callouts | 82 |
| Info / note / abstract callouts | 102 |
| Headings added | 167, across 113 notes |
| Notes with a Properties block | **0** |
| Unresolved links | **0** |
| Links pointing at a missing verse anchor | **0** |

## 2. What changed in this pass

- **Backlinks moved inline.** Links now sit in the sentence where you cite the
  verse — `In [[Jeremiah 29#^v11|Jeremiah 29:11]], In everything that I do…` —
  rather than in a list at the bottom. The old "Scripture Referenced" footers
  are gone.
- **Properties removed.** No note has YAML frontmatter any more, so Obsidian
  shows no Properties panel anywhere. For the Scripture Reference notes the
  provenance that used to live there (translation, source URL, retrieval date) is
  now a visible `[!abstract]` callout at the top of each note instead of being lost.
- **Colorized via Obsidian callouts.** Scripture quotations render as
  `> [!quote]` blocks with the reference as the clickable title; passage pointers
  and provenance render as `[!info]` / `[!abstract]`. These are native Obsidian
  callouts, so they pick up your theme's colors with no CSS needed.
- **Formatting.** ALL-CAPS section labels became real headings in title case;
  numbered section labels became `###` headings; tab-and-bullet lists became
  markdown lists; lead-in emphasis like `TOXIC MASCULINITY - …` became bold.
- **Invisible characters stripped.** 99 directional-override characters
  (U+202C / U+202D) were embedded in your pasted citations — e.g.
  `‭‭Matthew‬ ‭6‬:‭9‬-‭10‬` — which broke both rendering and any attempt to match the
  reference. Also removed 6 U+2028 line separators. This is why some citations
  previously refused to link.

## 3. Scripture sourcing

Every verse resolved at **Tier 1 — NLT retrieved from source**. No vault-quote
fallbacks, no placeholders.

- **Source:** biblegateway.com (NLT), retrieved 2026-09-02. Each reference note
  links its own source.
- **Scope:** only passages your notes actually cite — 230 verses. Full chapters
  for all 93 would be ~1,500+ verses, past fair-use limits for a copyrighted
  translation.
- **Method:** verse text *and verse numbers* parsed straight from the page markup.

> [!important] Do not let a model transcribe verse numbers
> An earlier attempt had a language model read the passage off the page. It
> silently misnumbered Matthew 18:32-35 — shifted by one, and merged two verses
> into one. It was caught by spot-checking single verses. The final pipeline
> removes the model from parsing entirely.

**Independent check.** Where you had already quoted NLT yourself, the retrieved
text matched your wording exactly: Luke 16:10 and Ecclesiastes 9:10 (*Do Well*),
Mark 8:34-38 (*Built Different*), Jeremiah 1:5-10 (*Higher — Called and Anointed*),
Ezekiel 36:26 and Psalm 23:1 (*World vs. Word*), Luke 7:9 (*Jesus is Amazed*),
Matthew 6:6 (*Prayer*).

## 4. Notes titled

| Old | New | Phrase it came from |
|---|---|---|
| `Devotionals/NT/Untitled.md` | **Galatians 2 — Resting in Grace** | "Resting in grace is hard for high-achievers." |
| `Devotionals/NT/Untitled 1.md` | **John 21 — Restored After Failure** | "Jesus restores us … despite failing so many times." |
| `Sermons/Sondays/Untitled.md` | **Luke 7 — Position, Posture, Principle** | its own three section headers |
| `Sermons/Sondays/Untitled 1.md` | **Mark 6 — Expectation and Unbelief** | "Expectation is a breeding ground for miracles." |
| `Squadron/Untitled.md` | **Judges 6 — You Are Not Weak** | "You're not weak." |
| `Squadron/Untitled 1.md` | **Acts 4 — Repentance as Responsibility** | "Repentance is our responsibility." |

`Sermons/Gravity/Untitled.md` (empty) was already deleted before this run.

## 5. Hand-formatted notes

Four notes had structure the automatic rules could not infer reliably, so they
were laid out by hand:

- **`Luke 7 — Position, Posture, Principle`** — the Pharisee/woman/Jesus contrast
  became a table; Position/Posture/Principle became `###` headings.
- **`You are God's Greatest Strategy`** — the seven D's became headings with their
  references beneath.
- **`Foreshadowing Redemption`** — the five offerings became headings with their
  attributes as lists.
- **`W8D55 - A Renewed Mind`** — the worksheet became bold questions with numbered
  answers.

## 6. Still your call

- [ ] **Two citations look mistyped.** `Luke 17:23` in *C04 — Change Priority,
      Lordship*: your quoted wording ("does not come with observation… the kingdom
      of God is in you") is **Luke 17:20-21**. And `Deuteronomy 26:6` in *Rhythms of
      Leadership* is about Egypt oppressing Israel, with no clear tie to the note.
      Both linked exactly as you wrote them.
- [ ] **Four notes are about a passage but never name it** — no citation was
      invented for them: *Performative Fig Tree* (the cursed fig tree),
      *Foreshadowing Redemption* (Leviticus offerings), *The Prodigal Brother & The
      Orphan Heart* (quotes "I will not leave you as orphans" unattributed; works
      from Luke 15), *Little Shepherd Boy — Part One* (quotes 1 Samuel 16-17
      throughout with no reference given).
- [ ] **`Designed to be Men` and `Where are the Men?`** are near-duplicates with the
      same six citations. Left as two notes.
- [ ] **`Genesis 2` + Abraham** in *Mark 6 — Expectation and Unbelief* — the note
      opens "In Genesis 2, God wanted to bless the earth. But Abraham's decision
      costs the blessing of the earth." Abraham appears from Genesis 12. Left as
      you wrote it.
- [ ] **14 reference-only chapters** have no verse text (cited as whole chapters):
      Genesis 2, 12, 15, 22 · Exodus 5 · Numbers 20 · Joshua 14 · 1 Samuel 16 ·
      Job 1, 32 · Matthew 13 · Mark 5 · Luke 7, 16 · John 21 · Acts 4, 10, 19.
      Add verses to any you want to read inside Obsidian.

## 7. Preserved exactly

Your wording was not corrected anywhere. Still intact: `stubborness`, `discople`,
`geniunely`, `natiom`, `Ther needs`, the unfinished "Legacy is your generosity is
someone's ", the unfinished "God works in divine timing. Don't", and the blank in
"he tore the veil that separates holy of holies, and _____".

The changes made were structural — headings, lists, callouts, links, and invisible
character removal — not editorial.
