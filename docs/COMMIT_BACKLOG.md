# Daily Commit Backlog

A queue of real work for this repo. A scheduled Claude Code agent takes the **top unchecked item**,
does it properly, verifies it, and commits. This repo is **submitted coursework** (a public
portfolio), so the work is to make it legible, not to change it.

## Rules the daily agent follows

1. **One item per run.** Finish it or leave it uncommitted.
2. **ADDITIVE ONLY.** The labs were graded. Allowed: READMEs, `.gitignore`, environment notes,
   dataset/provenance notes, removing clearly accidental junk (`.DS_Store`, `.ipynb_checkpoints/`,
   duplicate files). **Forbidden:** editing a lab solution, changing an algorithm or its output,
   re-running notebooks (stored outputs must not change), reformatting notebook source, renaming
   or moving notebooks. If a lab looks wrong, record it under "Observations" - do not fix it.
3. **Verify.** Confirm no `.ipynb` changed (`git diff --stat` shows only the files you meant to
   touch). Every command a README tells a reader to run must be one you ran or can see is correct.
4. **Describe only what the code does.** Read the notebook before writing about it.
5. **No filler.** No whitespace churn or substance-free edits. If nothing honest can be done, make
   no commit.
6. Stage named paths only (never `git add -A` / `.`). Conventional commit subject, ending with the
   `Co-Authored-By` trailer. Tick the item and append to the Log below in the same commit.

## Repo facts (verified 2026-11-13)

Nine lab folders plus `Labexam.ipynb`, one notebook each, all `python3` kernel, all with stored
outputs. Every import is standard library (`random`, `copy`, `heapq`, `re`, `itertools`, `math`),
so there is no `requirements.txt` to write - only a "Python 3, stdlib only" note. No committed
junk files found. No `.gitignore` and no README exist yet. Several labs read `input()`, so they
need an interactive session (Colab/Jupyter), not a headless run.

| Path | What the code does |
|---|---|
| `Lab-1/lab1.ipynb` | Tic-tac-toe (human `X` vs random-move computer `O`); 2-room vacuum-cleaner reflex agent |
| `Lab-2/Lab_2.ipynb` | 8-puzzle solved by iterative-deepening DFS (blank is `-1`, user enters start/goal) |
| `Lab-3/HillClimb.ipynb` | 8-puzzle steepest-ascent hill climbing, misplaced-tiles heuristic (blank is `0`) |
| `Lab-4/A*.ipynb` | 8-puzzle A* with Manhattan-distance heuristic (user enters start/goal) |
| `Lab-5/Propositional.ipynb` | Truth-table entailment check `KB ⊨ α` for `A → B` vs `A ∨ B` |
| `Lab6/Resolution.ipynb` | Resolution refutation over a FOL clause list ("John likes peanuts") |
| `Lab7/AlphaBeta.ipynb` | Alpha-beta pruning on a hard-coded game tree; prints value, path, pruned branches |
| `Lab8/ForwardChaining.ipynb` | Despite the filename: unification with occurs check on two expression pairs |
| `Lab9/ForwardChaining.ipynb` | Forward chaining on the "Robert is a criminal" rule |
| `Labexam.ipynb` | 3x3 vacuum grid simulation with a cap of at most 2 fully clean rows |

## Queue

- [ ] **B1 - Top-level `README.md` index.** Table of the ten notebooks (use the table above, but
      re-check each row against the notebook), the AI topic each demonstrates (uninformed search,
      local search, informed search, propositional logic, FOL resolution, adversarial search,
      unification, forward chaining), how to open them (Colab badge already in most notebooks, or
      Jupyter), and the "Python 3, stdlib only" note. State which labs need interactive input.
- [ ] **B2 - Per-lab READMEs, Labs 1-5.** `Lab-N/README.md` each: problem, how to run, example
      input that the stored output actually used, what the stored output shows.
- [ ] **B3 - Per-lab READMEs, Labs 6-9 and Labexam.** Same format. For Lab8 say plainly that it is
      unification (not forward chaining) and Lab9 is the forward-chaining one.
- [ ] **B4 - `.gitignore`.** `.ipynb_checkpoints/`, `.DS_Store`, `__pycache__/`, `.vscode/`,
      `.idea/`. Nothing tracked is affected.

## Observations for VB to decide (do NOT fix - graded work)

- **Lab-5 stored output has bogus symbols.** `extract_symbols` runs after `logical_replace`, so
  the regex picks up the Python keyword `or` and the glued token `BA` (from `kb + alpha`
  concatenation). Output shows `Symbols detected: ['A','B','BA','or']` and a 16-row table instead
  of 4. The final verdict (KB does not entail α) happens to be correct for `A → B` vs `A ∨ B`,
  but the table is not.
- **Lab6 ignores its `query` argument.** `resolution(kb, query)` overwrites `query` with a
  hard-coded `¬Likes(John, Peanuts)`.
- **Lab8 treats constants as variables.** `is_variable` is "lowercase string", so constant `b`
  unifies as a variable; stored result is `{'x': 'a', 'b': 'y'}`.
- **Naming is inconsistent:** `Lab-1`..`Lab-5` vs `Lab6`..`Lab9`; `Lab8/ForwardChaining.ipynb`
  is really unification; `A*.ipynb` has an asterisk in the filename. Renaming would alter the
  submission, so left alone.
- **Colab badges point at other repos:** Lab-2 to `MahediBuilds/AILab` (and `Lab_3.ipynb`), Lab6-9
  to `vikasShashi-dot/AI`. Provenance of those labs (pair work / shared template?) is something
  only VB can state; do not write a claim about it.
- **`LICENSE` copyright line reads "Buyyani"**, not VB. VB to confirm whether that is intended.
- **Lab-1 stored output** records a human-played tic-tac-toe game with random computer moves, so
  it is not reproducible.

## Log

2026-11-13 - audit - docs: add AI-LAB commit backlog from a full read of every notebook
