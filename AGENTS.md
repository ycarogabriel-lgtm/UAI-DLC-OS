# Repository Guidelines

## Project Structure & Module Organization

This repository is a Markdown training package, not an application. Start with `README.md` and use `INVENTARIO.md` to locate material. The numbered directories follow the training flow: `01-contexto/` introduces the approach, `02-preparacao/` and `03-facilitacao/` prepare the environment and facilitator, and `04-etapas/` holds the 14 stage guides. `05-insumos-ficticios/` contains simulated Aurora inputs; `06-projetos-em-andamento/` covers existing projects; `07-apoio/` contains supporting checklists and exercises. `08-origem/` records provenance and limits. Preserve the attribution and MIT license in `referencias/product-os-methods/`.

## Development & Validation

There is no build, package manager, or automated test suite. Preview changed Markdown in a renderer before submitting it. Check local links and numbering after moving or renaming files; for example, `rg -n '04-etapas/' README.md` finds stage links in the entry point. Review `README.md`, `INVENTARIO.md`, and any affected index when adding a document. Do not describe a linked tool or plugin as installed merely because its documentation appears here.

## Writing Style & Naming

Write training content in Portuguese, using clear headings, short paragraphs, and relative Markdown links for local files. Match existing directory prefixes and stage names, such as `04-etapas/09-refinamento-com-cliente.md`. Simulated inputs use stable `I##-` identifiers; their identifiers are not chronological order. Keep source claims, assumptions, human decisions, and fictional examples distinct. When changing a method excerpt, preserve its attribution and explain the source version.

## Review & Contribution Guidelines

There is no local Git history from which to infer a commit convention. If this package is placed under version control, use short imperative commit subjects that name the affected area, such as `docs: clarify Aurora handoff`. In a pull request, summarize the training change, list affected paths, note source or version changes, and state which links and rendered pages you checked. Include screenshots only when layout or visual references change.

## Training Material Safeguards

Keep facilitator material separate from participant inputs. Release only the current Aurora input during an exercise; the full kit reveals later decisions. Retain fictional-material notices, and never present simulated interviews, tests, approvals, or estimates as evidence from a real project.
