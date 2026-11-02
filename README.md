# Walkthrough data

One run = one evaluator walking one scenario on one product and platform.

## Naming
`runs/<scenario>-<product>-<platform>-<evaluator>.json`, lowercase and hyphenated.
Example: `runs/s1-chatgpt-web-gn.json`.

## Fields
| Object | Fields |
|---|---|
| `run` | `evaluator_id`, `scenario_id`, `platform_name`, `platform_type`, `date`, `product_version`, `account_state`, `interface_language`, `notes` |
| `step` | `step_id`, `screenshot`, `problems`, `notes` |
| `problem` | `what_happened`, `severity`, `guidelines`, `evidence`, `notes` |

`severity` is 0-4; `guidelines` is e.g. `["G1", "H3"]`; use `""`/`[]`, never `null`.

## Screenshots
`screenshots/<scenario>/<product>-<platform>/NN-name.png`; reference relative to JSON, e.g. `../screenshots/s1/chatgpt-web/01-open.png`.

## Problems
One problem per object; never merge two problems.
