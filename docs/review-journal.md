# Review Journal

The cases below are the review handles I would use before changing the implementation.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its backend services focus without claiming live deployment or external usage.

## Cases

- `baseline`: `queue pressure`, score 145, lane `ship`
- `stress`: `retry load`, score 227, lane `ship`
- `edge`: `worker slack`, score 153, lane `ship`
- `recovery`: `session drift`, score 205, lane `ship`
- `stale`: `queue pressure`, score 174, lane `ship`

## Note

A future change should add new cases before it changes the scoring rule.
