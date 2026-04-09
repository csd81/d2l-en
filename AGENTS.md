# Repository Guidelines

## Project Structure & Module Organization

This repository is the English source for the D2L book. Most content
lives in chapter markdown files such as `chapter_preliminaries/*.md`,
`chapter_optimization/*.md`, and `contrib/*.md`. Reusable framework
helpers are generated into `d2l/` (`torch.py`, `tensorflow.py`,
`jax.py`, `mxnet.py`). Shared site assets live in `static/`, figures in
`img/`, source diagrams in `graffle/`, and CI/build infrastructure in
`.github/` and `ci/`.

## Build, Test, and Development Commands

Use a dedicated Python or Conda environment for the framework you are
editing.

- `python setup.py develop`: install the local `d2l` package in editable mode.
- `pip install git+https://github.com/d2l-ai/d2l-book`: install the
  `d2lbook` build tool used by this repo.
- `d2lbook activate pytorch chapter_preliminaries/ndarray.md`: enable one
  framework tab while editing a chapter.
- `d2lbook activate all chapter_preliminaries/ndarray.md`: restore all tabs
  before committing.
- `d2lbook build lib`: regenerate saved helpers into `d2l/<framework>.py`.
- `jupyter notebook --NotebookApp.contents_manager_class='notedown.NotedownContentsManager'`:
  open `.md` chapters as notebooks for local execution.

GitHub Actions in `.github/workflows/ci.yml` runs multi-framework and
website/PDF builds, so keep changes small and easy to validate.

## Coding Style & Naming Conventions

Follow [STYLE_GUIDE.md](/home/rama/Desktop/d2l-en/STYLE_GUIDE.md).
Keep prose precise and consistent. For Python, follow PEP 8, prefer
single quotes, alphabetized imports, and short lines (target 78-79
characters). Reuse established variable names such as `X`, `y`,
`train_iter`, `test_iter`, `lr`, and `num_epochs`. In markdown source,
edit executable content through the notebook workflow rather than hand
patching rendered outputs.

## Testing Guidelines

Run the edited notebook locally with "Restart & Run All" before opening a
PR. When code is reused later, mark it with `#save` and rerun
`d2lbook build lib`. Ensure outputs stay consistent across framework tabs
when applicable.

## Commit & Pull Request Guidelines

Recent history favors short, imperative commit subjects such as `Update
lenet.md` or `Fixed uci.edu dataset link (#2591)`. Base work on `master`,
use a focused branch, and keep each PR scoped to one topic. For larger
changes, open an issue first. PRs should explain what changed, why it was
needed, and any chapter or framework impact; include screenshots only for
UI or rendered-page changes.

## Security & Contribution Notes

Do not open public issues for security concerns; follow
`CONTRIBUTING.md`. Licensing and contributor expectations are defined in
the root `LICENSE*` files and the main contribution guide.
