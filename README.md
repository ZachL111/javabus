# javabus

`javabus` explores backend services with a small Java codebase and local fixtures. The technical goal is to implement in-memory broker semantics with consumer groups and ack timeouts.

## Reason For The Project

The project exists to keep a narrow engineering decision visible and testable. For this repo, that decision is how queue pressure and worker slack should influence a review result.

## Javabus Review Notes

The first comparison I would make is `retry load` against `queue pressure` because it shows where the rule is most opinionated.

## What It Does

- `fixtures/domain_review.csv` adds cases for queue pressure and retry load.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/javabus-walkthrough.md` walks through the case spread.
- The Java code includes a review path for `retry load` and `queue pressure`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## How It Is Put Together

The implementation keeps the scoring rule plain: reward signal and confidence, preserve slack, penalize drag, then classify the result into a review lane.

The added Java path is deliberately direct, with fixtures doing most of the explaining.

## Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Check It

The check exercises the source code and the review fixture. `stress` is the high score at 227; `baseline` is the low score at 145.

## Boundaries

No external service is required. A deeper version would add more negative cases and a clearer boundary around invalid input.
