# TDTU presentation style spec (reusable)

Source analysed: `AYM_fakulteti_taqdimoti_2.pptx` (12 slides, 16:9, 12192000 × 6858000 EMU = 13.333" × 7.5").
Purpose of this file: so a later prompt does not have to re-derive the design. Re-read this before building a new deck in the same style.

## Reusable assets (session scratchpad)

| Path | What it is |
|---|---|
| `…/scratchpad/pptx_in/x/` | Full unpacked source deck (all 12 slides — copy whole slides from here as patterns) |
| `…/scratchpad/template_tdtu.pptx` | Stripped template: theme + 6 layouts + header/logo images + title slide + 1 SWOT content slide. Validates clean. |
| `…/scratchpad/pptx_in/slide-NN.jpg` | Rendered reference images of every source slide |

Scratchpad root: `/tmp/claude-0/-home-user-Dauitbay/38543552-2dd4-5442-b4ea-9f3fe2ebc11c/scratchpad`

**Method for a new deck: unpack `template_tdtu.pptx`, duplicate slides with the pptx skill's `add_slide.py`, edit `ppt/slides/slideN.xml`. Do NOT rebuild from scratch with pptxgenjs — the header image, logos and gradient title background only exist inside this package.**

## Theme — "TDTU kafedra"

| Role | Hex | Used for |
|---|---|---|
| dk2 / navy | `002060`, deep navy `1B2A6B` / `1A1F36` | section pills, body text color, dark cards |
| accent1 blue | `0255B3` | primary blue |
| accent6 blue | `2A7AC2` | header underbar left third, blue cards |
| accent3 cyan | `14A1D6` | header underbar middle third |
| accent2 teal/green | `28C8A0` | header underbar right third |
| green | `239B45` | "S / strengths", ILM-FAN category |
| orange | `F28C28` / `E87722` | "W / weaknesses", AKKREDITATSIYA |
| red | `C00000` / `D32030` | "T / threats", TIJORATLASHTIRISH, big KPI numbers |
| purple | `7A4FA3` | XALQARO HAMKORLIK |
| card fill | `EEF4FB` (also `EEF3FB` as lt2) | every light card / KPI tile background |
| white | `FFFFFF` | slide background, all header text |

**Fonts: Times New Roman everywhere** (major + minor). Every run writes `<a:latin typeface="Times New Roman"/>` explicitly.

## Layouts

- `slideLayout2.xml` — **TDTU_TITLE**: full-bleed blue gradient/dot background image; 3 logos across the top (Ministry of Higher Education 1051560,566928 · TDTU 4919472,612648 · Ministry of Transport 8595360,566928); centred title placeholder (idx 103) at 1097280,2331720 size 9994392×2103120, 28pt bold white centred; subtitle placeholder (idx 104) at 1700784,5760720, 18pt white centred ("TOSHKENT – 2026").
- `slideLayout3.xml` — **TDTU_CONTENT**: white background; `header.png` blue gradient band at 0,0 → 12191695×585216; under it a 73152-high tri-colour bar split in thirds (`2A7AC2` | `14A1D6` | `28C8A0`); TDTU logo at 9921240,54864 → 1938528×475488; title placeholder (idx 105) at 320040,45720 → 9418320×502920, left-aligned bold white.
  - On each slide the title is **overridden to 20pt bold white, Times New Roman, `anchor="ctr"`, at 274320,27432 → 8778240×530352**. Keep this identical on every content slide.
- Layouts 1, 4, 5, 6 are leftover Office defaults — ignore.

## Content canvas

- Content area starts at **y = 822960 EMU (0.9")**, left margin **274320 (0.3")**, right edge ≈ 11917680.
- Column grids seen: 2 (SWOT), 3 (results, strategy), 4 (kafedra cards), 5 (annual plan), 6 (KPI strip).
- Vertical/column separators are **dotted lines**, not solid bars.

## Shape vocabulary (copy these exactly)

1. **Card** — `roundRect`, `adj = 8000`, fill `EEF4FB`, outline `w="19050"` in the card's category colour. Body insets `lIns/rIns 73152`, `tIns/bIns 27432`, `anchor="ctr"`.
2. **Pill / category header** — `roundRect` with `adj = 50000`, solid category colour, no line, white bold text 15pt centred. Insets `54864 / 27432`.
3. **Header tab** — `roundRect` `adj≈18000–20000`, solid category colour, white bold 13–15pt, sits on top edge of its card (slides 7, 8, 12).
4. **Letter badge** — `ellipse` 960120×960120, solid category colour, white bold **40pt** single letter (S/W/O/T) centred, `lIns/rIns = 0`.
5. **Number badge** — small `ellipse` ~320000 wide, category colour, white bold ~12pt digit, top-left corner of a KPI card.
6. **KPI tile** — card + big number **28–40pt bold** in the category colour, caption under it **10–12pt bold** navy `1A1F36`, centred.
7. **Dark KPI bar** — `roundRect` filled navy `1B2A6B`, white bold number inside (slide 2's top strip uses one per colour).
8. **Chevron / process arrow** — `homePlate` / `chevron` preset, solid colour, white bold caps text (slides 6 and 12 monitoring row).
9. **Photo** — plain `rect` picture with rounded corners where used; always at the bottom of its card, full card width minus insets.

## Text rules

- Bullets are a **literal `▪ ` run coloured in the category colour, bold**, followed by the text runs — there is no `buChar`. Keep this pattern.
- Body text **14pt**, `b="0"`, colour `1A1F36`; key figures and terms inside the sentence are the same size with `b="1"` (sometimes coloured red `C00000` for emphasis).
- Paragraph spacing: `<a:spcAft><a:spcPts val="300"/></a:spcAft>` on every bulleted paragraph.
- Captions under KPI numbers: 10–12pt bold, centred.
- Titles are ALL CAPS, no trailing period.
- Language: Uzbek Latin (with ‘ apostrophes) — some legacy slides mix Cyrillic. Match the source file's language of the new data.

## Slide inventory of the source (patterns to reuse)

| # | Pattern | Reuse for |
|---|---|---|
| 1 | Title (3 logos, gradient) | cover |
| 2 | 6 KPI strip + 4 colour-coded department cards with photo | org overview |
| 3 | Dense infographic: KPI row + 8 sub-panels | youth/social affairs |
| 4 | 3 columns (dotted dividers), KPI grid + bullets + photo strip | achievements |
| 5 | SWOT 2×2 with circle letter badges | analysis |
| 6 | Left goal column + 6 numbered colour cards (01–06) | strategy / directions |
| 7 | 4 columns: tab + photo + bullets + flagship footer | research directions |
| 8 | 5-column annual plan, each item a card with a date chip | yearly roadmap |
| 9–10 | Row list: icon + navy label + description + value chip + green "Spin-Off" pill | commercialisation |
| 11 | Org chart with connectors + right photo/value list | structure |
| 12 | 10 numbered KPI cards + 4-step chevron monitoring row | targets & monitoring |

## Build + QA checklist

```bash
S=/root/.claude/skills/synced/5f538fe2-3326-4c1d-ad47-1e232bc96956_d4cf1da8-a437-47db-bc04-f0a2611f4c27/pptx
python3 $S/scripts/add_slide.py unpacked/ slide2.xml --after slideN.xml   # duplicate, before editing content
(cd unpacked && rm -f ../out.pptx && zip -Xqr ../out.pptx .)
python3 $S/scripts/office/validate.py out.pptx --original template_tdtu.pptx
python3 $S/scripts/office/soffice.py --headless --convert-to pdf out.pptx && pdftoppm -jpeg -r 100 out.pdf slide
```
Then look at every rendered slide: overflow, overlap, leftover text from the copied slide.

## Deck 2 — Aviation faculty (rebuilt 2026-10-13)

Data source: `_____13.10.2026_-compressed.pptx` (16 slides) plus the image-rich variant the user sent
second. Output: `AVIACIYA_fakulteti_taqdimoti.pptx`.

**Two rules the user set, both binding on any future edit:**
1. **Words are verbatim.** Every sentence, lab name, equipment line and price is copied
   character-for-character from the source deck. Nothing is translated, shortened, re-ordered inside a
   sentence, or invented. Slides that would need invented content (targets, monitoring) are not added.
2. **Format = 16 slides, one per source slide, same order.** Nothing merged, nothing split. The TDTU
   card styling of deck 1 is the skin; the source deck is the skeleton.

Slide map (new → source): 1→1 title · 2→2 faculty · 3→3 yutuqlar · 4→4 lab base photo grids ·
5→5 Aviation Engineering labs · 6→6 aviasozlik 5 labs · 7→7 radioelektron 2 labs ·
8→8 computer design (космик) · 9→9 CubeSat · 10→10 pilot training + DUAL · 11→11 infrastructure,
staff, aircraft, simulators · 12→12 aircraft · 13→13 simulators · 14,15,16→14,15,16 strategy.

Photos: extracted from the source deck into `…/scratchpad/assets` (lab01–lab32 from source slide 4,
pl01–pl06 aircraft, sim01–sim03 simulators) and placed centre-cropped via `lib.pic`/`fit_crop`.

**Generator bug fixed 2026-10-13 — do not reintroduce:** `<a:spcPct>` takes THOUSANDTHS of a
percent (90% = `90000`). Writing `val="90"` makes PowerPoint collapse every line of a paragraph on
top of the next, while LibreOffice silently clamps it — so the visual QA render looked fine and the
real file was unreadable. `lib.para()` now multiplies the `line` argument by 1000. Any new OOXML
percentage field (spcPct, spcPts aside) needs the same check.

Generator: `…/scratchpad/gen/{lib.py,slides.py,build.py}` — `python3 gen/build.py` rebuilds the deck
(copies assets into the package, writes rels, validates, zips).

## Status

- [x] Source deck analysed, template extracted, spec written
- [x] Aviation deck rebuilt verbatim, 16 slides matching the source one-for-one, photos included, validated and visually QA'd (16/16)
