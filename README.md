# javabus

`javabus` is a focused Java codebase around implement in-memory broker semantics with consumer groups and ack timeouts. It is meant to be easy to inspect, run, and extend without a hosted service.

## Javabus Walkthrough

I would read the project from the outside in: command, fixture, model, then roadmap. That keeps the backend services idea grounded in files that can be checked locally.

## Reason For The Project

I use this kind of project to make a rule visible before adding more machinery around it. The important part here is not the size of the codebase. It is that the input signals, scoring rule, fixture data, and expected output can all be checked in one sitting.

## Where Things Live

- `src`: primary implementation
- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands

## Capabilities

- Includes extended examples for queue pressure, including `recovery` and `degraded`.
- Documents bounded workers tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.
- Adds a repository audit script that checks structure before running the language verifier.

## How It Is Put Together

The design is intentionally direct: parse or construct a signal, score it, classify it, and verify the expected branch. This makes the repository useful for studying backend services behavior without needing a service or database unless the language project itself is SQL. The Java implementation uses a compact package layout and direct assertion checks.

## Getting It Running

Install Java and run the commands from the repository root. The project does not need credentials or a hosted service.

## Data Notes

The extended cases are not random smoke tests. `degraded` keeps pressure on the review path, while `recovery` shows the model when capacity and weight are strong enough to clear the threshold.

## Command Examples

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Check The Work

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Possible Extensions

- Add a loader for `examples/extended_cases.csv` and promote selected cases into the language test suite.
- Add a short report command that prints the score breakdown for a single scenario.
- Add malformed input fixtures so the failure path is as visible as the happy path.
- Add one more backend services fixture that focuses on a malformed or borderline input.

## Tradeoffs

The examples cover useful edges, not every edge. A larger version would add malformed-input tests, richer reports, and deeper domain parsers.
