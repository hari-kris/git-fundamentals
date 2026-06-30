# Git to GitHub — Faculty Workshop

A 2-hour workshop package introducing Git and GitHub fundamentals to college faculty who are starting their first version control journey. Built for **Vels Institute of Science, Technology & Advanced Studies (VISTAS)**.

The material takes faculty from the history and purpose of version control through Git fundamentals, branching, GitHub collaboration features, and how to mentor students using Git/GitHub for assignments, projects, and interview-ready portfolios — with real-world academic examples (question papers, lab manuals, syllabus revisions, research drafts) connecting every concept.

## Contents

| File | What it is |
|---|---|
| [`index.html`](index.html) | The live, interactive slide deck (48 slides). Self-contained HTML/CSS/JS — open it directly in any browser, no build step or internet connection needed. |
| [`cheatsheet.md`](cheatsheet.md) | A standalone Git command quick-reference faculty can keep open or print separately during/after the workshop. |
| [`workshop-handout.html`](workshop-handout.html) | A print-formatted version of the full workshop content (concepts, examples, diagrams, and the command reference) as a leave-behind document. |
| [`workshop-handout.pdf`](workshop-handout.pdf) | The rendered, printable PDF of the handout above — ready to share or print for attendees. |

## Using the slide deck

Open `index.html` in a browser and navigate with the keyboard:

- `→` / `Space` — next slide
- `←` — previous slide
- `Home` / `End` — jump to first / last slide
- On quiz slides, press `Enter` or `Space` to reveal the answer before moving on

The deck covers, in order: the history and purpose of version control, the story of Git, Git vs. other source control tools, Git vs. GitHub, core Git fundamentals (the three areas, daily commands, branching and merging, remotes, undoing changes), GitHub collaboration features (Issues, Projects, Pull Requests, Actions, Pages), how to mentor students on Git/GitHub workflows and portfolio-building, and an 8-question recap quiz.

## Regenerating the PDF handout

The PDF is rendered from `workshop-handout.html` using headless Chrome:

```bash
google-chrome --headless --no-sandbox --disable-gpu --disable-dev-shm-usage \
  --print-to-pdf="workshop-handout.pdf" --no-pdf-header-footer \
  "file://$(pwd)/workshop-handout.html"
```

Re-run this after editing `workshop-handout.html` to refresh the PDF.

## Workshop details

- **Audience:** Faculty, first version control journey
- **Duration:** 2 hours
- **Level:** Basic → medium fundamentals
- **Goal:** Use Git/GitHub confidently for personal and academic work, and mentor students through Git/GitHub for coursework, projects, and campus-interview portfolios
