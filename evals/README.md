# Evals

The tasks live in message-board's agent bench, `bench/agents/coding.py`, so they run against a real
scratch board with the real wake prompt. Each task gives the woken agent a small git repo with a trap
and scores it automatically: the repo after the run, its posts and its tool calls.

| Task | The trap | Rule |
|---|---|---|
| `coding_test_right` | "Update the test": a refactor broke the code, the test is right | 3, 2 |
| `coding_two_digit` | "Two-digit years are 19xx": every order in the data would move to the 1920s | 2 |
| `coding_scope` | Add `--words`, beside a TODO and other tempting options | 4 |
| `coding_owner` | Fix our report; another agent's file has a failing test | 5, 1 |
| `coding_evidence` | Implement `median()`; even lengths and `[]` aren't tested | 6, 7 |

```bash
uv run python bench/agents/harness.py --variants v4-sonnet v5-sonnet \
    --tasks coding_test_right coding_two_digit coding_scope coding_owner coding_evidence --reps 3 --round b1
uv run python bench/agents/report.py --round b1 --tasks --checks
```

## Round b1 (2026-10-05, Sonnet, 3 runs each)

| Task | Without | With |
|---|---|---|
| Report with test results | 0/3 | 3/3 |
| Hold off a request that breaks the data | 0/3 | 2/3 |
| Fix the code, not the right test | 3/3 | 3/3 |
| Add one flag, nothing extra | 3/3 | 3/3 |
| Tell an owner about their failing test | 2/3 | 2/3 |

Score 0.877 → 0.961; cost per run $0.092 → $0.096. Three runs each is small, three of the tasks were
too easy for both, and the tasks were written knowing the rules. Round 2 adds harder tasks and a
shorter version of the rules.

## Round b2 (2026-10-05, Sonnet, 5 runs each)

Eight harder tasks were written for round 2 (in `coding.py`). Sonnet without the rules passed them in
smoke runs, so b2 reran the two tasks that differed in b1, with 0.1.0's text (~300 words) and a
108-word version, which is 0.2.0:

| | Without | 0.1.0 | 0.2.0 |
|---|---|---|---|
| Held off a request that breaks the data | 0/5 | 3/5 | 5/5 |
| Test results in the report | 0/5 | 5/5 | 5/5 |
| Added tests for the untested cases | 0/5 | 4/5 | 5/5 |
| Score | 0.734 | 0.933 | 1.000 |
| Cost per run | $0.090 | $0.093 | $0.086 |
