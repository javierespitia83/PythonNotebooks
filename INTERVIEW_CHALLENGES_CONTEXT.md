# Python Interview Challenge Bank — Context

## Purpose
A 5th track, separate from PCEP/PCAP/ATBS/Effective Python: a single standalone notebook of the Python coding challenges most commonly asked in technical interviews. Not tied to any exam syllabus — built from cross-validated real-world frequency, not assumption.

## File
`python_interview_challenges.ipynb` — no track prefix (like `bash_scripting_fundamentals.ipynb`, this is a standalone reference, not part of a numbered book/exam sequence).

## Methodology (per Javier's explicit instruction: validate before building)
1. Ran multiple web searches on "most common Python interview coding challenges" across general prep sources (InterviewBit, GeeksforGeeks, LeetCode-style roundups, career-prep blogs).
2. Cross-checked against a real, popular curated practice repository: [devAmoghS/Python-Interview-Problems-for-Practice](https://github.com/devAmoghS/Python-Interview-Problems-for-Practice) (990+ GitHub stars), fetched via raw README — a table of 60+ named, file-backed problems.
3. Kept only challenges that repeated across **both** general web search results **and** the GitHub practice repo — i.e., genuinely, repeatedly asked, not a single source's opinion.

## Content structure — 26 challenges in 5 categories
- **A. Strings (8):** reverse string, palindrome check, anagram check (+ group anagrams), first non-repeating character, character frequency count, reverse words in a sentence, balanced parentheses/brackets, string compression (RLE).
- **B. Arrays/Lists (9):** FizzBuzz, Two Sum, find duplicates, remove duplicates preserving order, find missing number, find max/min without built-ins, move zeroes to end in-place, merge two sorted lists, flatten nested list.
- **C. Numbers/Math (4):** Fibonacci (recursive/iterative/memoized — with complexity discussion), factorial (recursive), prime check + Sieve of Eratosthenes, numeric palindrome check.
- **D. Algorithms (3):** binary search (iterative + recursive), bubble sort, quicksort.
- **E. Data Structures (2):** Stack (list-backed), Queue (deque-backed, with a note on why not a plain list).

## Format
Same reading-first philosophy as the rest of the project: each challenge has a "**Asked as:**" (realistic phrasing), "**What it tests:**" (the underlying concept/trap being probed), and a fully written, verified, runnable solution with printed test cases — never TODO placeholders.

## Verification
Built via a generator script (`md_cell`/`code_cell`/`notebook` pattern, consistent with every other notebook in this project), then executed via `python3 -m nbconvert --to notebook --execute --inplace`. Result: 26/26 code cells executed with zero errors (confirmed programmatically by scanning all cell outputs for `output_type == "error"`).

## History
- 2026-08-05: Built after Javier asked about common Python interview coding challenges, then explicitly requested validation against real repeated-frequency sources before building — see project memory `project_interview_challenges_plan` (or equivalent memory file).
