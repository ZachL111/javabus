# Field Notes

I would read this project from the data inward: cases first, implementation second.

The domain cases cover `queue pressure`, `retry load`, `worker slack`, and `session drift`. They sit beside the smaller starter fixture so the project has both a compact scoring check and a domain-flavored review check.

`stress` tells me the happy path still works. `baseline` tells me whether the guardrail still has teeth.

The language-specific addition keeps the review model in a package class with direct assertions.
