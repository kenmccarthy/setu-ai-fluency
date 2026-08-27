# SETU GenAI Programme — Course 3: AI Fluency

A self-paced, ~1-hour web course on critically evaluating, adapting and shaping
practice in an AI-enabled university. Aimed at all SETU staff who have completed
**Course 1 — AI Literacy** and **Course 2 — AI Competency**. Built on the same
template as Courses 1 and 2, so all three read as one continuous programme.

## What it is

A **standalone static website** — plain HTML, CSS and JavaScript with **no build step
and no dependencies**. It runs by opening a file in a browser and can be hosted anywhere
(GitHub Pages, the SETU web server, an intranet folder, or an LMS as an embedded/uploaded
package).

## Two ways to distribute — one source

The same `index.html` + `assets/` power **both**:

1. **Standalone website** — host the folder anywhere (GitHub Pages, the SETU web
   server, an intranet). Nothing to build.
2. **SCORM package for your LMS** — run `python3 scorm/build_scorm.py` to produce
   `dist/setu-ai-fluency-scorm-1.2.zip`, then upload it to Moodle/Brightspace/etc.
   The LMS tracks progress, resume position and completion. See **`scorm/README.md`**.

The SCORM adapter (`assets/js/scorm.js`) is inert without an LMS, so the website version
is unaffected and the two never diverge.

```
index.html             The whole course (cover + 10 sections + completion)
assets/css/styles.css   Design system (SETU brand tokens at the top — shared with Courses 1 & 2)
assets/js/course.js     Navigation, progress, activities, spectrums, ratings, reflection
assets/js/scorm.js      SCORM 1.2 adapter (no-op outside an LMS)
assets/js/certificate.js Learner-generated certificate of completion
assets/fonts/           Self-hosted DM Sans + Inter (brand fonts) + fonts.css
scorm/                  Build script + packaging docs
assets/img/             SETU logo assets (light/dark) + favicon — course images are still
                        placeholders, see docs/CONTENT-TODO.md
docs/CONTENT-TODO.md    Checklist of images and SETU-specific content still to insert
```

## Branding

Built to the **SETU Brand Guidelines (v1, May 2022)**, matching Courses 1 and 2:
- **Colour** — Slate Grey `#435465` primary with **Barrow Blue** as this course's
  accent (Course 1 uses Sea Green, Course 2 uses Clover — each course in the
  programme takes its own colour from the SETU secondary palette). All tokens live
  at the top of `assets/css/styles.css`.
- **Typography** — DM Sans (headings) and Inter (body), self-hosted in `assets/fonts/`
  so the course is fully self-contained and works offline.
- **Logo** — master logo in the top bar (with a white variant that swaps in for dark
  mode) and on the cover; the crest symbol as the favicon.

## Sections

Course Introduction · Questioning AI · Rethinking Practice · Human–AI Collaboration ·
Evaluating AI Tools and Emerging Technologies · AI Agents and Increasing Autonomy ·
Leading Responsible Change · AI, Equity, Sustainability and the Human Future · From
Individual Fluency to Collective Capability · The Fluency Challenge · Continuing the
Journey — plus a cover and a completion screen. Content is drawn from the course
script, *AI Fluency: Shaping Practice in an AI-Enabled University*.

## Features

- **Progress bar** that remembers the furthest point reached (saved in the browser).
- **Contents panel** for jumping between sections; collapses to a drawer on mobile.
- **Interactive activities**, each drawn from the script:
  - **Confidence self-rating** — 1–5 scale on five statements, taken at the start and
    repeated at the end, with an inline "started at X · now Y" comparison.
  - Progressive-reveal scenarios — "The amazing new AI tool" (EduSmart AI), "The
    enthusiastic manager", "Whose voice is missing?" — decide, then reveal each new
    fact or consideration in turn.
  - A three-option spectrum ("The Human–AI Continuum") and two four-option spectrums
    ("Automate, augment, rethink or retain?", "How much autonomy?") with discussion
    notes per row.
  - An 11-dimension tool-evaluation checklist and a three-way tool comparison
    ("Choose the tool").
  - A nine-step capstone framework ("The Fluency Challenge") — Purpose through
    Evaluate — reusing the same `.steps` component as Course 2's five-step framework.
  - A "sphere of influence" multi-part reflection (Me / Us / SETU).
- **Reflection notes** — spread across the course, autosaved locally, downloadable as
  a single text file at the end.
- **Certificate of completion** — the learner enters their name and downloads a branded
  certificate (print / save as PDF); the LMS also records completion via SCORM.
- Accessible (keyboard nav, skip link, focus states, reduced-motion support),
  responsive, light/dark aware, and printable to PDF.

This course deliberately does **not** reuse two components from the Course 1/2
template: role-pathway tabs (the Fluency script is thematic, not role-differentiated)
and the click-the-flag error-detection activity (no section presents a passage with
planted errors to find). It does add one small, additive CSS piece — a four-option
variant of the spectrum component (`.srow__opts--4`) — for the two activities that
need four choices instead of three.

## Run it locally

Just open `index.html` in a browser. Or serve the folder:

```bash
python3 -m http.server 8000    # then visit http://localhost:8000
```

## Before it goes live — SETU to complete

The narrated content is in place from the script. **Every image in this course is
still a placeholder** (a dashed box), because no photography or illustrations have
been supplied yet. See **`docs/CONTENT-TODO.md`** for the full list, suggested sizes,
and a few other open items (two resources referenced in the script that don't exist
yet, the certificate/credits wording, and a design note on the re-themed accent
colour worth a quick visual check).

## Branding tokens

All colours live as CSS variables at the top of `assets/css/styles.css`
(`--brand` = Slate Grey, `--accent` = Barrow Blue for this course, secondary palette,
tints, etc.) — same structure as Courses 1 and 2, so changing them there updates each
course's look independently (each course is its own repo; token changes are applied
per repo, not shared automatically). Fonts are defined in `assets/fonts/fonts.css`.

## Notes

- In the **website** version, progress, ratings and reflections are stored in the
  visitor's own browser (`localStorage`) — nothing personal leaves the device.
- In the **SCORM/LMS** version, completion, progress and resume position are reported to
  the LMS for record-keeping (notes still stay on the device). Rebuild the package with
  `python3 scorm/build_scorm.py` after any content edit.
- This course reuses the interactive components built for Courses 1 and 2 (AI
  Literacy, AI Competency) — spectrum activities, progressive-reveal scenarios,
  stepped frameworks, multi-part reflections — so all three courses feel like one
  continuous programme, with one small additive four-option spectrum variant.
