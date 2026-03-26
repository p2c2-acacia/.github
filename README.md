# .github

Organization-level GitHub configuration for P²C² Acacia.

## What's here

- `profile/README.md` — Organization profile page (rendered at [github.com/p2c2-acacia](https://github.com/p2c2-acacia))
- `.github/workflows/update-readme.yml` — Auto-updates the game challenges table daily from public repos tagged `game-challenge`
- `.github/workflows/check-repo-tags.yml` — Validates that all org repos follow the tagging convention

## Repo Tagging Convention

Every repo in the organization must have exactly one category topic:

| Topic | Use for | Additional requirements |
|-------|---------|------------------------|
| `game-challenge` | Game challenge repos | Must also have a `p2c2-XXXX` topic |
| `game-project` | Game project repos (e.g., game-alpha) | None |
| `misc` | Everything else (this repo, tooling, docs) | None |

The `p2c2-XXXX` topic encodes the 4-dimension classification (A=Deterministic/Stochastic, B=Observability, C=Agents, D=Environment). Example: `p2c2-0001` = deterministic, fully observable, single agent, dynamic.

## Auto-updating challenge table

The `update-readme.yml` workflow runs daily at 6 AM UTC and on push to `main`. It queries the GitHub API for public repos with topic `game-challenge` and regenerates the table between `<!-- GAME-CHALLENGES-START -->` and `<!-- GAME-CHALLENGES-END -->` markers. Do not manually edit content between those markers.

To add a new game challenge to the table: make the repo public and add topics `game-challenge` and `p2c2-XXXX`. The table will update on the next workflow run.
