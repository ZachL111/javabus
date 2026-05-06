# Javabus Walkthrough

I use this file as a small checklist before changing the Java implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | queue pressure | 145 | ship |
| stress | retry load | 227 | ship |
| edge | worker slack | 153 | ship |
| recovery | session drift | 205 | ship |
| stale | queue pressure | 174 | ship |

Start with `stress` and `baseline`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

`stress` is the optimistic case; use it to make sure the scoring path still rewards strong signal.
