# Data Portfolio — Brahmantya Fikri Setya Putra

Personal portfolio site for a Data Analyst / Data Scientist / Business Analyst.
Single-page, no build step, no dependencies: `index.html` carries its own CSS and JS.

**Live:** https://mydataportfolio-six.vercel.app

## Running it

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

## Layout

```
index.html          the whole site — markup, styles and scripts in one file
assets/             images used by the page
  img/              case-study visuals (pr-*), photos (p-*), logos, certificates
  source/           unused originals kept for reference
Project/            source material behind each case study
.gitattributes      line-ending rules (data files kept byte-exact)
```

### Asset naming

| Prefix | Meaning | Example |
| --- | --- | --- |
| `pr-` | Project visual shown in a case drawer | `pr-axa-1.webp` |
| `p-` | Photograph (internship, organisation) | `p-telkomsel-1.jpg` |
| `logo-`, `cert-` | Organisation logo, certificate | `logo-telkomsel.png` |
| `hero-` | Hero portrait and medal, with WebP variants | `hero-portrait-1400.webp` |

Case-study visuals are WebP, max 1600px wide, quality 88.

## Adding a project

Each project is one `<button class="work">` in `#workList`. The case drawer, the
cursor preview, the filters and the command palette all read from its data
attributes, so adding the button is most of the work:

| Attribute | Purpose |
| --- | --- |
| `id` | `p<n>`, referenced by the chart and the skills ledger |
| `data-cat` | `analytics`, `ml`, `nlp` or `genai` — drives the filters |
| `data-title`, `data-kind`, `data-role`, `data-year` | Case drawer header |
| `data-metric` | The outcome, shown in the drawer |
| `data-stack` | `|`-separated tools |
| `data-desc` | Full case text |
| `data-imgs` / `data-caps` | `|`-separated paths and captions — **must be the same length** |

Then add a matching entry to the `PTS` array in the script so the project appears
in the impact/depth chart and the search index, and update the counts in the
section heading, the `#workCount` badge and the capability cards.

## Conventions

Every number on the page traces back to something in `Project/` — a report, a
notebook or a dataset. If a figure can't be sourced, it doesn't go on the page.
