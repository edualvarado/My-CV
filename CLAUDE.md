# CLAUDE.md - My-CV

## Purpose
Personal LaTeX CV and cover letters for Eduardo Alvarado, built on a fork of
[Awesome-CV](https://github.com/posquit0/Awesome-CV) (`upstream` remote). The only
document that matters is `examples/cv-eduardo-alvarado.tex`; everything else is either
upstream demo material kept for reference or per-application cover letters. Output PDFs
are committed so the latest CV is always downloadable from GitHub.

## Navigation
| Path | Contents |
|------|----------|
| `examples/cv-eduardo-alvarado.tex` | **Main CV** — preamble, personal info, section `\input` order |
| `examples/cv/ea/*.tex` | The real CV content, one file per section (`-ea` suffix = mine) |
| `examples/awesome-cv.cls` | **Customized class actually used** — adds `\cvpublication`, `\cvskillnobreaktwo`, `cvitemone` |
| `awesome-cv.cls` (root) | Stock upstream class (CRLF). Used only by `Makefile` + `test.tex` — do not edit |
| `examples/publications.bib` | BibTeX (19 entries), used by cover letters via biblatex — **not** by the CV |
| `examples/coverletter-eduardo-alvarado-*.tex` | Per-employer cover letters (Apple, Google, MPI-IS, Neura, …) — **gitignored** |
| `examples/cv.tex`, `resume.tex`, `cv/*.tex`, `resume/` | Upstream demo files, untouched |
| `.vscode/tasks.json` | Build tasks (see below) |
| `Makefile` | Upstream demo builds only (`make examples`) — does not build my CV |

## Tech Stack
- **XeLaTeX** (required — `fontspec`/`fontawesome5`), **Biber** for cover-letter bibliography
- Document class: `awesome-cv` (forked), `hyperref`, `geometry`
- VS Code + LaTeX Workshop; recipes defined in `.vscode/settings.json`
- GitHub Pages via `_config.yml` (jekyll-theme-cayman)

## Conventions
- **Build** from inside `examples/` (the class file and `cv/` inputs resolve relative to it).
  VS Code task `XeLaTeX + Biber Build` = xelatex → biber → xelatex → xelatex; task
  `Clean LaTeX Files` removes aux files.
- **Edit content in `examples/cv/ea/*.tex`**, never in the main `.tex` — that file only
  configures the preamble and the `\input` order (sections are commented in/out there).
- Section files follow a fixed skeleton: `SECTION TITLE` banner → `\cvsection{...}` →
  `CONTENT` banner → `\begin{cventries}` with `%---` separators between entries.
- **Publications are hand-written** as `\cvpublication{authors}{title (+ icon links)}{venue, year}`
  in `publications-ea.tex`; my name is `\textbf{\underline{Eduardo Alvarado}}`. Icon links use
  `\faIcon{github|file-alt|youtube}`. `publications.bib` is a separate, cover-letter-only source —
  updating one does not update the other.
- Layout is hand-tuned with explicit `\vspace{...}` and `\newpage`; after any content change,
  recompile and check page breaks before committing.
- **Commit the rebuilt PDF** (`examples/cv-eduardo-alvarado.pdf`) together with the `.tex` change.
- Palette is documented in the preamble comments; accent is `\definecolor{awesome}{HTML}{283477}`.
- Commit messages in this repo: `UPDATED: CV`, `CHANGED: Publications`, `CHANGED: Fix`.

## Current Focus
Keeping the CV current for research positions in human motion / avatar synthesis (CV-ML-Graphics).
Recent commits are content refreshes to `publications-ea.tex` and `education-ea.tex`.

## Extended Context
- Upstream template: https://github.com/posquit0/Awesome-CV (license CC BY-SA 4.0 / LPPL for the class)
- Origin: git@github.com:edualvarado/My-CV.git
