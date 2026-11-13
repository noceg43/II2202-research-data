# Walkthrough data

One run = one evaluator walking one scenario on one product and platform.

## Layout
- `reference/`: ID sources. `guidelines.json` (guidelines + severity, from `docs/evaluation-framework.md`), `tasks.json` (scenarios, steps, paths, from `docs/task-analysis.md`)
- `runs/`: one JSON per run
- `screenshots/`: images referenced by runs
- `docs/`: evaluation framework and task analysis (prose, source of truth)

## IDs
- `guidelines`: IDs from `reference/guidelines.json` (`G1`, `G4`, ...).
- `scenario_id`: `S<n>`; `step_id`: `S<n>-A<NN>` (e.g. `S2-A06`), both from `reference/tasks.json`.
- Paths are `S<n>-P<n>` (e.g. `S1-P2`); walk the steps in the order listed for the path.
- New scenario or step? Add it to `docs/task-analysis.md` and `tasks.json` together. Never renumber or reuse an ID; append new ones.

## Naming
`runs/<scenario>-<product>-<platform>-<evaluator>.json`, lowercase and hyphenated.
Example: `runs/s1-chatgpt-web-gn.json`.

## Fields
| Object | Required | Optional |
|---|---|---|
| `run` | `evaluator_id`, `scenario_id`, `platform_name`, `platform_type` (`web`/`mobile`), `date` | `product_version`, `account_state`, `interface_language`, `notes` |
| `step` | `step_id`, `screenshot` | `problems`, `notes` |
| `problem` | `what_happened`, `severity`, `guidelines` | `evidence`, `notes` |

`severity` is 0-3 (see `reference/guidelines.json`); `guidelines` is e.g. `["G1", "G4"]`. Leave optional fields as `""`/`[]`, never `null`.

## Screenshots
`screenshots/<scenario>/<product>-<platform>/NN-name.png`; reference relative to JSON, e.g. `../screenshots/s1/chatgpt-web/01-open.png`.

## Problems
One problem per object; never merge two problems.

## Adding a run
1. Copy `runs/s1-chatgpt-web-gn.json` and rename it per **Naming**.
2. Fill `run`.
3. Add screenshots under **Screenshots**.
4. Add one `step` per step walked, using IDs from `reference/`.
