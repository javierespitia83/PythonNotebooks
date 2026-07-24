# PythonNotebooks — Effective Python Review Context

**Goal:** move from "I know Python syntax" (covered by the PCAP/PCEP track) to "I write idiomatic, effective Python" — following *Effective Python: 125 Specific Ways to Write Better Python* by Brett Slatkin. This is the third track in the project, alongside PCAP/PCEP ([[project_pcap_notebook_plan]]) and Automate the Boring Stuff ([[project_atbs_notebook_plan]]).

**Edition used:** 3rd edition (Pearson Addison-Wesley, November 2024) — the current edition at [effectivepython.com](https://effectivepython.com/), fetched 2026-07-18. It covers Python through 3.13 and expands from the 2nd edition's 90 items to **125 items across 14 chapters**, adding two new chapters (Robustness, Performance) plus C-extension/native-library coverage.

**Format:** same reading-first philosophy as the ATBS and PCAP/PCEP tracks — real explanation grounded in the book's actual advice, plus complete, verified-runnable example code per item. One notebook per book chapter; markdown headers use the book's own item numbers (e.g. `### Item 17 — Prefer enumerate over range`) for easy cross-reference back to the source text.

## Chapter → notebook mapping

| # | Notebook | Chapter | Items |
|---|----------|---------|-------|
| 1 | `ep_01_pythonic_thinking.ipynb` | Pythonic Thinking | 1–9 |
| 2 | `ep_02_strings_slicing.ipynb` | Strings and Slicing | 10–16 |
| 3 | `ep_03_loops_iterators.ipynb` | Loops and Iterators | 17–24 |
| 4 | `ep_04_dictionaries.ipynb` | Dictionaries | 25–29 |
| 5 | `ep_05_functions.ipynb` | Functions | 30–39 |
| 6 | `ep_06_comprehensions_generators.ipynb` | Comprehensions and Generators | 40–47 |
| 7 | `ep_07_classes_interfaces.ipynb` | Classes and Interfaces | 48–57 |
| 8 | `ep_08_metaclasses_attributes.ipynb` | Metaclasses and Attributes | 58–66 |
| 9 | `ep_09_concurrency_parallelism.ipynb` | Concurrency and Parallelism | 67–79 |
| 10 | `ep_10_robustness.ipynb` | Robustness | 80–91 |
| 11 | `ep_11_performance.ipynb` | Performance | 92–99 |
| 12 | `ep_12_data_structures_algorithms.ipynb` | Data Structures and Algorithms | 100–107 |
| 13 | `ep_13_testing_debugging.ipynb` | Testing and Debugging | 108–115 |
| 14 | `ep_14_collaboration.ipynb` | Collaboration | 116–125 |

## Working conventions
- English only, reading-first: one item = one markdown explanation (why this practice, what it fixes) + at least one runnable, verified example.
- Some items in chapters 9 (Concurrency) and 11 (Performance) touch platform-specific or environment-specific behavior (GIL-bound timing, C-extension compilation, hardware-dependent benchmarking) — where sandbox execution isn't meaningful, the code is still real and correct, with a note on what to expect on a real machine.
- Any item requiring a Python version newer than what's available for verification is flagged explicitly in that notebook's setup note.

## Verification done (2026-07-18)
All 14 notebooks (125 items, 125 code cells total) executed end-to-end with `nbconvert --execute` — zero errors across the entire track. Every new library/technique was tested for runnability before being written into a notebook, following the same methodology established on the ATBS track:

- **Fully executed for real**, including some unusually deep verification: Item 96 (Extension Modules) actually compiles a real C extension (`fastmath.c`) via `setuptools`/`gcc` and imports the compiled `.so`; Item 79 (`ProcessPoolExecutor`) genuinely runs work across separate processes and the notebook confirms the wall-clock speedup; Item 75-78 (asyncio) genuinely runs concurrent coroutines and confirms the timing.
- **Notebook-environment-specific fix applied**: `asyncio.run()` cannot be called from a Jupyter kernel (it already has a running event loop) — Chapter 9's items use top-level `await` instead, with an explicit note that a plain `.py` script should use `asyncio.run(main())` as the book shows.
- **Adapted, not skipped**: `unittest.main()` normally calls `sys.exit()`, which would kill the kernel — Chapter 13's items call `unittest.main(argv=['ignored'], exit=False)` instead, with a note that plain `unittest.main()` is correct in a real test file.
- **Illustrative with a clear note**: Item 114 (`pdb`) needs a human typing into an interactive prompt, which an auto-executed notebook can't provide — demonstrated by feeding `pdb` scripted commands programmatically, with the real `breakpoint()`-based usage shown as a comment for Cursor's interactive kernel.
