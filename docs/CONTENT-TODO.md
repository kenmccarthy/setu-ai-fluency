# Content to insert before go-live — SETU checklist

The course content and interactions are in place, built from the *AI Fluency:
Shaping Practice in an AI-Enabled University* script. The items below are what's
still needed before go-live. Search the codebase for `figure__slot` to find every
image slot, and `[SETU to confirm]` for the open text items.

## 1. Images (you are supplying these)

Every slot is a `<figure class="figure">` with a dashed placeholder — none of this
course's images exist yet. To fill one, replace the inner
`<div class="figure__slot">…</div>` with `<img class="figure__img" src="assets/img/your-file.jpg"
alt="…">` (plus an optional `<figcaption>`). Recommended: SETU photography style
(shallow depth of field, natural light, authentic, inclusive), matching Courses 1 & 2.
Suggested sizes below (all can be larger; keep the aspect ratio).

| Section | Where | Suggested size / ratio |
|---|---|---|
| Course Introduction | Banner under the hero | 1600×540 (3:1) |
| 1. Questioning AI | Header illustration | 1200×675 (16:9) |
| 2. Rethinking Practice | Header illustration | 1200×675 (16:9) |
| 3. Human–AI Collaboration | Header illustration | 1200×675 (16:9) |
| 4. Evaluating AI Tools and Emerging Technologies | Header illustration | 1200×675 (16:9) |
| 5. AI Agents and Increasing Autonomy | Header illustration | 1200×675 (16:9) |
| 6. Leading Responsible Change | Header illustration | 1200×675 (16:9) |
| 7. AI, Equity, Sustainability and the Human Future | Header illustration | 1200×675 (16:9) |
| 8. From Individual Fluency to Collective Capability | Header illustration | 1200×675 (16:9) |
| 9. The Fluency Challenge | Header illustration | 1200×675 (16:9) |
| 10. Continuing the Journey | Reflective/closing image | 1200×675 (16:9) |

## 2. Downloadable / linked resources referenced in the script but not yet available

- [ ] **SETU AI Tool Evaluation Checklist** (Section 4, "Evaluating AI Tools and
  Emerging Technologies") — currently rendered as a dashed `.placeholder` block.
  Replace with a real download link once the checklist exists.
- [x] **SETU Assessment Redesign Framework** link (Section 2, "Rethinking Practice" —
  the Assessment redesign case study) — resolved, links to https://arf.genain3.ie.

## 3. Completion / certificate

- [ ] **Certificate wording** — reads "Course 3 — AI Fluency: Shaping Practice in an
  AI-Enabled University". If you want a signatory line (e.g. a name/title) or a
  QR/verify note, say so and it can be added. The learner types their own name; the
  LMS also records completion via SCORM.

## 4. Attribution (done)

- [x] The `.credits` line on the Done screen names the script author (Dr Hazel
  Farrell) and credits ChatGPT-generated images, matching Course 2's convention.

## 5. Branding (done — confirm)

- [x] Built on the same template, tokens and terminology as Courses 1 & 2:
  **courses + sections** (no "module"/"stage"/"hub" as structural terms).
- [x] SETU logo, Slate Grey + secondary palette, DM Sans/Inter fonts (copied from
  Course 2's `assets/`).
- [x] Accent colour set to **Barrow Blue** (`--accent-base: var(--barrow-blue)`), the
  third colour from the SETU secondary palette (Course 1 = Sea Green, Course 2 =
  Clover).
- [x] **Design review already applied:** `--info` (used for info callouts) is
  independently fixed to Barrow Blue, and the spectrum activity's middle option was
  originally hardcoded to Barrow Blue too — once the accent became Barrow Blue, that
  option looked too similar to the first ("Automate"/"Human-led") option. Fixed by
  moving the spectrum's middle-option colour to Suir Blue instead (`styles.css`,
  `.srow__opts button[data-v="1"]` and `.spectrum__legend span:nth-child(2)`) — a
  one-line-per-rule change, unrelated to the accent token itself. Worth a final
  visual check once real content/images are in place.
- [ ] Optional: replace the extracted PNG logos with official **SVG/EPS** vector files
  (same optional item as Courses 1 & 2).

## 6. Simplifications made versus the Course 1/2 template (for future maintainers)

- This course does **not** use the `.pathway`/`.ptab` role-tabs component — the
  Fluency script is thematic, not role-differentiated (no Teaching/Assessment/
  Research/Professional Services/Leadership split in the source script).
- This course does **not** use the `.trust`/`.flag` click-the-error component — no
  section of the script presents a passage with planted errors to detect (that's
  Course 2's territory).
- A new `.srow__opts--4` CSS modifier was added to `styles.css` to support two
  four-option activities ("Automate, augment, rethink or retain?" in Section 2 and
  "How much autonomy?" in Section 5) — the template's spectrum only shipped a
  three-option variant. `course.js`'s spectrum handler needed no changes; it's
  already option-count-agnostic.

## 7. Optional / general

- [ ] AI working group to review all sections for accuracy and SETU tone.
- [ ] Accessibility sign-off against SETU's WCAG target.
- [ ] After any edit, rebuild the SCORM package: `python3 scorm/build_scorm.py`.
