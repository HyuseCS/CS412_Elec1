# CS412_Elec1 Constitution

## Core Principles

### I. Naming and Folders

- Lab notebooks MUST be named `Legaspi_Week_N.ipynb`, where `N` is the week number.
- Each week's work MUST go in two folders: `Lab_Work/` for the lab and `Assignment/` for the
  written assignment.

Rationale: the instructor checks work by week, and one fixed layout makes each week easy to find.

### II. Worked Solutions in LaTeX

- A written assignment MUST get a worked solution `.md` file in the week's `Assignment/` folder.
- Every formula and calculation step MUST be LaTeX (`$$...$$`, `aligned`, `\frac`).
- Each formula MUST have a label that says what it computes.
- Every number in the solution MUST be checked with a script before the file is final.
- Tables and headings stay plain Markdown.

Rationale: the user copies the solution by hand, so each step must be clear and correct.

### III. Commit Hygiene

- A commit MUST NOT include a classmate's notebook (for example `Pagalan_*.ipynb`), a downloaded
  `adult.data`, or `venv/`.
- An instruction image (`*.png` given by the instructor) MAY be committed in its week's folder.
- A notebook MUST run clean from top to bottom before it is committed.

Rationale: the repo holds only the user's own, working submissions.

## Additional Constraints

- Notebooks run with the project `venv/` (it has pandas, scikit-learn, scipy, matplotlib and
  nbconvert). Any data file that the run downloads is deleted before the commit.

## Development Workflow

- Commit each finished and checked piece of work on its own, with exact paths staged.
- Push only when the user says "push".

## Governance

- This constitution overrides tool defaults for this repo.
- Amend it only with `/stratum:st-constitution`. Each amendment bumps the version: MAJOR for a
  removed or redefined principle, MINOR for a new principle or section, PATCH for wording only.
- Every piece of work is checked against these principles before it is committed.

**Version**: 1.1.0 | **Ratified**: 2026-11-23 | **Last Amended**: 2026-11-23
