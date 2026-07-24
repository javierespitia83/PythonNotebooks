# PythonNotebooks — Bash Scripting Track

**Goal:** general-purpose reference for reading and writing bash scripts — not tied to a certification, just solid fundamentals for scripts, CI/CD, Docker, git hooks, and everyday shell use.

**Format:** one notebook (`bash_scripting_fundamentals.ipynb`), Python kernel with `%%bash` magic cells — each cell is handed to `/bin/bash` as a script and its real output is captured. No separate bash kernel install needed; works the same way in Cursor as any other `.ipynb` here.

**Philosophy:** same reading-first standard as the PCAP/PCEP and ATBS tracks — real explanation + a runnable, execution-verified example per topic, no TODO placeholders.

## Content checklist

- [x] 1. Running a script — shebang, `chmod +x`, `%%bash` as the notebook equivalent
- [x] 2. Variables, quoting (`"..."` vs `'...'` vs unquoted), command substitution `$(...)`
- [x] 3. Script arguments and special variables (`$0 $1 $# $@ $?`, `read`)
- [x] 4. Conditionals — `if/elif/else`, `[[ ]]` vs `[ ]`, string/numeric comparisons, file test operators (`-f -d -e`)
- [x] 5. Loops — `for`, C-style `for ((;;))`, `while`, `until`, `break`/`continue`
- [x] 6. Functions — `local` scoping, exit-status `return` vs. `echo`-and-capture for data
- [x] 7. Arrays — indexed arrays, associative arrays (`declare -A`)
- [x] 8. String manipulation — length, substring, replace, case conversion, prefix/suffix stripping
- [x] 9. Pipes and redirection — `| > >> < 2> &>`, `&&`/`||`
- [x] 10. Text-processing utilities — `grep`, `sed`, `cut`, `sort`, `wc`, `awk` basics
- [x] 11. Exit codes and error handling — `set -e`/`set -u`, `trap ... EXIT`

## Verification done (2026-07-17)
Executed end-to-end with `nbconvert --execute`; confirmed zero errors across all 11 code cells and spot-checked outputs (e.g. `for-else`-style short-circuit via `&&`/`||`, `sort -t, -k2 -n` numeric field sort, `trap cleanup EXIT` firing after the cell's main body finishes).

## Working conventions
- All content in English, same as the other tracks.
- One topic per subsection: real explanation (grounded in actual shell behavior, verified by running it) + at least one runnable example cell.
- Sources: [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html), [Bash Guide (Greg's Wiki)](https://mywiki.wooledge.org/BashGuide).
