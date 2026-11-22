# site-generator-speed-01

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/zqzqzq68/site-generator-speed-01/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/zqzqzq68/site-generator-speed-01/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0 (make.fun's own static site
generator), written for the make.fun bounty
site-generator-speed-01-run-20261122.

## What it does

`solve.js` exports `run(input)`, which returns exactly the output tree
makefun-site 1.0.0's `build` returns for the same input: every page's
`index.html`, the index and tag pages, `build-report.txt` and each static
file, byte for byte — its front matter, template dialect, Markdown subset,
slug rule and report all reproduced.

## How it is faster

- Every template is compiled once per build into a JavaScript function, so
  rendering is straight-line code instead of a walk over a node tree.
- Markdown is rendered in one fused pass (no token array), and plain text is
  escaped in bulk instead of a character at a time.
- Slugs are cached per build, and word counts are taken with a single
  allocation-free scan instead of a regular expression match.

## Layout

- `solve.js` — the generator. Dependency-free ES module, `run(input)`.
- `main.ts` — the driver the harness runs: reads `/input/cases.json`,
  answers each case with `run`, writes `/output/answers.json`.

## Run it

```sh
node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=daring-condor-23&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
