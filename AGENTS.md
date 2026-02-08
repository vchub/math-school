# Repository Guidelines

## Context

We teach math in school
Our general approach:

- We focus on making a student to work by themselves
- Concise explanation
- Example of problem with analyzed and explained solution
- Several analogues problems as exercise
- A mix of typical/route problems and 1 non-typical, complex problem

## Instructions

- Act as school math teacher
- Use Russian for the output docs.
- Be critical, check your assumption, use web search

## Project Structure & Module Organization

- `algebra/`, `combinatorics/`, and `old/` hold lesson content in MyST Markdown (`.md`). Chapter files follow a hyphenated pattern like `ch1-three-different-problems.md`.
- `combinatorics/images/` and `images/` store figures referenced by lessons.
- `_build/` is generated output from `myst build` (do not edit by hand).
- `misc/` contains notebooks and drafts; treat as experimental.
- `myst.yml` configures the MyST/Jupyter Book build.

## Build, Test, and Development Commands

- we use uv, not pip
- `myst build` builds the site into `_build/site/`.
- Optional (when using `pyproject.toml`): `uv sync` installs pinned dependencies from `uv.lock`.

## Coding Style & Naming Conventions

- Use MyST Markdown for lesson content; keep headings short and descriptive.
- Use hyphenated, lowercase filenames (e.g., `ch12-pascals-triangle.md`).
- Keep YAML in `myst.yml` to 2-space indentation.
- Prefer relative image paths like `images/foo.png` or `combinatorics/images/bar.png`.

## Testing Guidelines

- There are no automated tests in this repo.
- Treat `myst build` as the validation step; fix any build warnings before submitting changes.

## Commit & Pull Request Guidelines

- Commit history uses short, lowercase, imperative-style messages (e.g., `add exercises`, `fix readme`).
- PRs should describe the scope of content changes and list affected chapters (paths).
- Include screenshots of rendered pages when modifying layout, figures, or build settings.

## Configuration & Content Tips

- Python requirement in `pyproject.toml` is `>=3.13`; ensure your environment matches.
- Keep new content inside the relevant subject folder; avoid adding files directly at repo root unless they are config.
