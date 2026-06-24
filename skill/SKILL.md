---
name: quebec-parish-register
description: >-
  Transcribe and translate 19th-century Quebec Catholic parish registers —
  handwritten actes de baptême, mariage, and sépulture — from photographs into a
  structured Markdown document with a typed-French transcription plus an English
  translation of every entry. Use this skill whenever someone shares images of
  old French-language Catholic church/sacramental records (baptisms, marriages,
  burials, often marked B/M/S, signed by a curé or vicaire) and wants them
  transcribed, translated, read, typed up, or deciphered
  — including casual asks like "what does this old church record say?", French
  requests like "transcris ces actes", a single hard-to-read entry, or a batch of
  leaves sent without naming the task. Also use to append leaves to a register
  already started this way, and to handle the certification page and
  back-of-register index. Do NOT use for modern French documents, OCR of printed
  text, non-genealogical handwriting (recipes, notes), audio transcription, or
  building family trees/GEDCOM from existing data.
---

# Quebec parish register transcription & translation

## What this produces

For each register, a single continuous Markdown document containing, in order:

1. A **title block** naming the parish, year, and officiating clergy.
2. The **court certification** page (often in English; transcribe as-is).
3. One **section per leaf**, each holding its entries in register order.
4. Each **entry** rendered as a typed-French transcription **and** an English translation.
5. A **glossary** of recurring terms and formulas.
6. The register's own **alphabetical index** (if photographed), as finding-aid tables.

The goal is a faithful scholarly transcription a genealogist can search and cite — not a loose paraphrase. Preserve every name, date, place, occupation, and relationship.

These registers follow rigid notarial formulas, so most of the work is reading the handwriting and the proper names correctly; the surrounding boilerplate is predictable. Read `references/formulas.md` for the standard entry templates (French + English) before transcribing your first entry, and keep `references/glossary.md` open for term equivalents. Use `assets/document-template.md` as the skeleton for a new register.

## Core conventions

**Three independent series.** Baptisms (**B**), marriages (**M**), and burials/sépultures (**S**) are each numbered in their own sequence (B.1, B.2…; M.1, M.2…; S.1, S.2…). A leaf usually mixes all three. The margin of each entry gives its letter, number, and the subject's name — use that as the heading.

**Leaf headers are authoritative for leaf order.** Most pages carry a written leaf number in the top corner ("Twenty seventh leaf"). Trust that over your own count and over the back-of-register index (the index's leaf numbers are an approximate finding aid and are sometimes off by one).

**Expand standard abbreviations silently**, but don't invent content. "ptre" → prêtre, "ptre vic." → prêtre vicaire, "Mgr" → Monseigneur, etc. Keep the priest's signature line as written (e.g., "J. A. Moreau, ptre vic.").

**Mark uncertain readings with `[?]`** immediately after the doubtful word, especially surnames, given names, and place names — these are what genealogists most need and most often can't verify elsewhere. Better an honest `Bourgon[?]` than a confident wrong guess.

**Record the clerk's own corrections.** Phrases like *un mot rayé nul* (one crossed-out word void), *un mot interligné bon* (one interlined word valid), and *un renvoi en marge bon* (one marginal insertion valid) are part of the legal record — keep them in both the French and English.

**Note margin-vs-body name conflicts** rather than silently picking one. The margin sometimes names a child "Édouard" while the body says "Évariste"; flag it in a short note so the user can judge.

**Preserve signatures.** When parties signed, list the signatures as they appear ("Adéline Crépeau / J. E. Plamondon / … / H. C. Hamelin, ptre"). When they couldn't, keep the formula (*qui n'ont pas signé* / *qui n'ont pu signer* — the later vicar often uses the latter; both mean "did not / could not sign").

## Per-entry format

Use a level-3 heading with the series letter, number, and subject, then labelled French and English paragraphs:

```markdown
### B. 77 — François Dion

**French:** Le onze août mil huit cent soixante-six, nous prêtre soussigné avons
baptisé François, né la veille, du légitime mariage de Dominique Dion,
cultivateur, et de Célina Levasseur, de cette paroisse. Parrain François Dion et
marraine Vitaline Levasseur, qui, ainsi que le père, n'ont pas signé. J. A. Moreau, ptre

**English:** On the eleventh of August 1866, we the undersigned priest baptized
François, born the day before, of the lawful marriage of Dominique Dion, farmer,
and Célina Levasseur, of this parish. Godfather François Dion and godmother
Vitaline Levasseur, who, like the father, did not sign. J. A. Moreau, priest
```

When an entry **spans two leaves** (common for long marriage acts), transcribe it whole under the leaf where it begins and add a one-line note: `> *Entry begins on the Twenty-fourth Leaf and concludes on the Twenty-fifth.*`

## Cross-references and consistency checks

These registers are internally redundant, and using that redundancy catches transcription errors:

- **Infant baptisms are often followed weeks later by the infant's burial.** When you see a burial that matches an earlier baptism (same parents, plausible age), add a note: `> *Burial of the infant baptized in B. 75 — born 4 Aug., died 7 Aug.*` Likewise link spouses to their marriage act and parents to their own burials.
- **Verify number sequences run cleanly.** If two leaves both seem to claim S.34, something is misread or misordered. Use the firm anchors — entries whose numbers and dates are unambiguous — to pin down the sequence, then work outward.
- **When a number genuinely can't be reconciled, flag it; don't force it.** If the firm chain leaves no slot for an entry (e.g., a burial dated between S.33 and S.34 with no free integer), record the entry without a forced number and add a note explaining the conflict. The original clerks made numbering slips; an honest note serves the genealogist better than a fabricated number.
- **Watch for a change of officiant.** A new vicar's signature appearing partway through is worth a one-line note in the document, since it helps date and locate leaves.

For the full reasoning method on ordering out-of-sequence photo batches, see `references/ordering-leaves.md`.

## Incremental workflow (the default)

Users typically photograph a register a few leaves at a time and send batches over multiple turns. Maintain **one** document per register and **append** each new batch into it.

1. **First batch:** create `<Parish>_Register_<Year>.md` from `assets/document-template.md`. Fill the title block and certification, then add the leaf sections you have.
2. **Each later batch:** read the existing file, transcribe the new leaves, and insert them in the correct position. New leaves almost always belong just before the glossary, so insert at the anchor:
   ```
   ---

   ## Glossary
   ```
   Place the new `## … Leaf` sections immediately above that line. If a batch fills a gap between existing leaves, insert it in chronological position instead.
3. **Reconcile across the seam.** A new batch frequently completes an entry left hanging at the end of the previous batch, or forces a renumbering you couldn't see before. Re-check the cross-leaf continuation chains and the B/M/S sequences each time, and fix earlier entries if the new evidence demands it (note what you changed when you report back).
4. **Keep the glossary growing.** Add any new occupations or formulas the batch introduces (e.g., *sellier* = saddler, *meunier* = miller).

After each batch, present the updated file and give a short summary of what was added and any corrections made.

## The certification page

The opening (and sometimes closing) leaf is a prothonotary's certificate stating how many leaves the register contains and that it's sealed for the year. In Quebec these are frequently in **English** already — transcribe as-is and note "no translation needed," expanding abbreviations (P.C. = Prothonotary, etc.) and recording any law stamp or seal. If it's in French, give French + English like any other entry. Watch out for a certification that belongs to a *different* register accidentally interleaved — confirm parish and year match the entries before trusting it.

## The alphabetical index

Many registers end with the clerk's own A–Z tables (Baptêmes, Mariages, Sépultures), each listing names with leaf numbers. If photographed, transcribe them as Markdown tables under a final `## Alphabetical Index` section. State clearly that the numbers are the **index's own leaf numbers** (approximate) and that where an index name differs from an entry body, the entry body is authoritative. The marriage table is short and worth doing in full; the baptism table is long and the hardest to read, so mark it best-effort with `[?]` on doubtful readings.

## Translation guidance

Translate into clear, period-appropriate English that mirrors the structure of the act without modernizing it away. Render dates written out in words as digits ("mil huit cent soixante-six" → "1866"; "le vingt-trois novembre" → "On the twenty-third of November"). Keep relationship and status terms precise — *fils majeur* = "of-age son," *fille mineure* = "minor daughter," *feu/feue/défunt(e)* = "the late." `references/glossary.md` lists the standard equivalents; reuse them consistently so the whole document reads as one hand.
