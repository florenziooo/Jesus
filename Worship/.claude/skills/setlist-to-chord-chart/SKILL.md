---
name: setlist-to-chord-chart
description: Turns a worship setlist (session/song list with assigned singers, keys, sections, and transitions) into a copyable Markdown Nashville-number-system chord chart, researching each song's chords on the web and transposing to the requested keys. Use this whenever the user pastes or describes a worship setlist and wants chords, a chord chart, a number chart, or a "number system" version — including requests like "chart this setlist," "give me the numbers for these songs," "what key should this be for altos," or a list of songs with singers/keys/sections that clearly wants a playable chart back, even if the words "chord chart" never appear.
---

# Setlist → Number-System Chord Chart

Turn a worship setlist into an accurate, copyable Nashville-number-system chart. The single most
important thing this skill protects is **accuracy over completeness** — a wrong chord in a live
worship set is worse than an honest "I couldn't verify this." Every rule below exists in service
of that.

## Reading the setlist correctly

A setlist entry like `Washed — Adrian` means **Adrian is the singer assigned to lead that song**,
not the artist who wrote or recorded it. Never write the singer's name as if they were the
original artist, and never let the singer's name bias which recording/arrangement you search for
— it's a scheduling detail, not a musical one.

To figure out which actual song/version is meant, use this priority order:
1. A link the user gave you for that song
2. Artist info the user gave you
3. Lyrics or section names the user mentioned (these narrow down the arrangement)
4. General worship context (e.g. this is clearly a contemporary congregational set, not a hymnal
   arrangement)
5. Reliable web sources, if none of the above resolve it

If you genuinely can't tell which version is meant (e.g. two unrelated songs share a title and
nothing in the setlist disambiguates them), say so and ask or state your best guess with a
caveat — don't silently pick one and chart it as fact.

## Researching chords

For any song whose chords the user hasn't already given you, use WebSearch/WebFetch to find the
progression. Ultimate Guitar, Worship Chords/Tabs, PraiseCharts, and official artist or church
resources are generally the most reliable. A couple of things matter more than just finding *a*
chord chart:

- **Confirm it's the right version.** Titles collide constantly in worship music — cross-check
  the lyrics in the source against what the user described (or against a lyric video/official
  recording) before trusting its chords.
- **If the user gave you a URL, that's the authoritative source** for that song — use it as
  primary and only deviate if it's obviously wrong (e.g. it's clearly a different song).
- **Cross-check when you can.** If two reputable sources disagree on a progression, don't just
  pick one silently — note the discrepancy and use whichever matches the specified
  version/arrangement, or flag it if you can't tell.
- **Never fabricate a progression.** If you search and can't find or verify chords for a
  requested section, say so explicitly rather than inventing something plausible-sounding. A
  guess that "sounds right" is exactly the failure mode this skill exists to avoid.

## Converting to the Nashville Number System

Map the confirmed chords in the confirmed key to scale-degree numbers:

| Chord quality | Number |
|---|---|
| I | `1` |
| ii | `2m` |
| iii | `3m` |
| IV | `4` |
| V | `5` |
| vi | `6m` |
| vii° | `7dim` |

Slash chords carry the bass note's scale degree: `C/E` → `1/3`, `G/B` → `5/7`, `F/A` → `4/6`.
Preserve inversions and passing chords exactly as they appear in the source — a `1 5/7 6m` line
is musically different from `1 5 6m`, and collapsing it to the simpler form throws away real
information the band needs. Don't reduce a distinctive bridge or turnaround progression to a
generic four-chord loop just because it's close to one.

## Keys

- An explicit user-specified key always wins over whatever key the source chart is in — transpose
  the progression accordingly (the number-system shorthand itself doesn't change; only the
  resulting pitches would, if you were to spell it out in letters).
- If a whole session is marked with a key "throughout," every song and transition in that session
  uses that key, even if the original recordings are in different keys — don't drift back toward
  each song's "natural" key.
- If asked for a key suited to a voice type (e.g. "give me a key for altos"), reason from the
  song's common/original key and the melody's apparent range, then recommend a practical key in a
  common worship key (concert pitch, usually a key guitarists/keyboardists like: G, A, C, D, E,
  B, etc.). State it plainly, e.g. `**Suggested alto key:** G`, and note that it's a practical
  recommendation based on a typical range for that voice type — not a claim about the specific
  singer's actual range, which you don't know.

## Only chart what's requested

If the user asks for just a bridge, or "bridge/verse 4," chart only those sections — don't pad
the response with the full song. This keeps the output usable as a real chart a musician reads
from, rather than a reference document they have to search through.

## Section labels

Label every section with its first lyric line, in this form:

```
### Verse — "Standing here in Your presence"
```

...followed by a fenced ` ```text ` block with the number-system chords, one chord-line per
musical line/measure grouping as it appears in the source. Use this pattern for Verse (numbered
if there's more than one — Verse 1, Verse 2...), Pre-Chorus, Chorus, Post-Chorus, Bridge, Tag,
Instrumental, Intro, Outro, and Transition. If a section repeats later in the same song, you can
label it `### Chorus — "..." (repeat)` and either restate the block or note "same as above" —
whichever keeps the chart easy to follow without pointless duplication.

## Stitching songs together

When a setlist chains songs into one continuous flow (a song feeding into another song's bridge,
etc.), chart it as one flow, not as isolated songs. Mark the handoff with its own header:

```
### Transition → The Blood
```

If the songs share a key, keep the chart in that key straight through rather than re-establishing
it. Only add a passing/turnaround chord at a transition if the source material actually has one
or it's clearly musically necessary to land in the next section (e.g. the last chord of song A
doesn't resolve toward song B's first chord) — don't invent an elaborate transition progression
for its own sake.

When the setlist offers **alternative** next songs (e.g. "from here, go either to At the Cross or
Name Above All Names"), present each as its own clearly separated option — never merge them into
one sequence the band would read as mandatory:

```
### OPTION A — At the Cross
...

### OPTION B — Name Above All Names
...
```

## Output format

Produce one clean, copyable Markdown document:

```markdown
# [Setlist Title]

---

# Session 1 — [Session Name]

## [Song Title]

**Singer:** [Name]
**Key:** [Key]                          <!-- or **Suggested [voice] key:** [Key] -->

### Verse — "[first line]"

​```text
1 4 5 6m
​```

### Chorus — "[first line]"

​```text
1 4 6m 5
​```

---

## [Next Song Title]
...
```

Use `## Transition → [Next Song]` or `### Transition → [Next Song]` headers inline where the
flow calls for it, and `### OPTION A/B — [Song]` for alternatives, per above. This vault already
has a worked example at [`Worship/DAY 2 — AFTERNOON WORSHIP SETLIST.md`](../../../DAY%202%20—%20AFTERNOON%20WORSHIP%20SETLIST.md)
— match that structure and tone when in doubt.

End with a short `# Sources` section — just enough to say where each song's version/chords were
confirmed (a URL if the user supplied one, otherwise the site you used). Keep citations out of
the chart itself; they belong here, not inline in the chord blocks.

## Before responding, check

- Every singer name is treated as the assigned singer, never mistaken for the artist
- The song/version identified matches the best available evidence (link > artist info > lyrics >
  context > web search), and any real ambiguity was flagged rather than guessed past
- Any user-supplied chord URL was used as the primary source for that song
- User-specified keys (including session-wide keys) were followed throughout
- Voice-type key recommendations were stated explicitly where asked for, with the "practical
  recommendation, not a fact about this singer" caveat
- Chords are correctly numbered, minor chords use `m`, and meaningful slash chords/inversions are
  preserved rather than simplified away
- Only the requested sections are included — no unrequested full-song padding
- Multi-song flows are stitched with transition headers; alternative flows are kept separate
- Every section is labeled with its actual first lyric line
- Nothing was fabricated — anything unverifiable is flagged instead of guessed
- The output is one clean Markdown document, ready to paste as-is
