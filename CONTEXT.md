# PythonNotebooks — PCAP-31-03 Review Context

**Goal:** review Python deeply enough to pass the **PCAP – Certified Associate in Python Programming** exam (`PCAP-31-03`, Python Institute), and to read/validate AI-generated Python code with real understanding.

**Format:** one Jupyter notebook per official exam section, written in English, opened and run in Cursor. Each notebook mixes markdown explanations with runnable code cells.

**Philosophy (revised 2026-07-11):** the first version of these notebooks used TODO placeholders for Javier to fill in himself — he found that didn't actually serve studying (no explanation, no examples to learn from). Rebuilt with the same reading-first philosophy as the Automate the Boring Stuff track: **real explanations grounded in the official Python docs, plus complete, verified-runnable example code** per subsection. Explanations are written from scratch per topic — no assumption that a subsection is "just a reminder."

**Source of truth:** [official Python Institute PCAP-31-03 syllabus](https://pythoninstitute.org/pcap-exam-syllabus) ([PDF](https://pythoninstitute.org/assets/627e61fa6fe27591613128.pdf)), fetched 2026-07-11. 40 exam items, single/multi-select + coding + scenario-based, passing score ≥70%. Explanations cross-checked against [docs.python.org](https://docs.python.org/3/) (math, random, platform, exceptions, classes/inheritance, input/output).

Also, as of 2026-07-17: [official Python Institute PCEP-30-02 syllabus](https://pythoninstitute.org/pcep-exam-syllabus) — PCAP's prerequisite exam, 4 blocks. Fetched in full after Javier flagged that he kept finding gaps himself ("siento que estoy haciendo la validacion yo"), so this was a complete one-shot syllabus review rather than another reactive patch.

## Exam blueprint → notebook mapping

**Naming convention (updated 2026-07-18):** every notebook across all four PythonNotebooks tracks now follows `<prefix>_<NN>_<description>.ipynb`, where `<prefix>` identifies the source (`pcep`, `pcap`, `atbs`, `ep`) and `<NN>` is that source's own chapter/block number — matching the pattern already used by the ATBS (`atbs_01`…`atbs_24`) and Effective Python (`ep_01`…`ep_14`) tracks. The old `00a`–`00d` / bare `01`–`05` filenames were renamed accordingly; content is byte-for-byte unchanged, only the filenames moved.

**PCEP-30-02 prerequisite blocks:**

| # | Notebook | Official PCEP block | Items | Weight |
|---|----------|----------------------|-------|--------|
| 1 | `pcep_01_fundamentals.ipynb` | Block 1 — Computer Programming and Python Fundamentals | 7 | 18% |
| 2 | `pcep_02_control_flow.ipynb` | Block 2 — Control Flow | 8 | **29%** (heaviest PCEP block) |
| 3 | `pcep_03_data_collections.ipynb` | Block 3 — Data Collections (Tuples, Dictionaries, Lists, Strings) | 7 | 25% |
| 4 | `pcep_04_functions_and_exceptions.ipynb` | Block 4 — Functions and Exceptions | 8 | 28% |

**PCAP-31-03 exam sections:**

| # | Notebook | Official section | Items | Weight |
|---|----------|-------------------|-------|--------|
| 1 | `pcap_01_modules_and_packages.ipynb` | Modules and Packages | 6 | 12% |
| 2 | `pcap_02_exceptions.ipynb` | Exceptions | 5 | 14% |
| 3 | `pcap_03_strings.ipynb` | Strings (+ list methods, §3.4) | 8 | 18% |
| 4 | `pcap_04_oop.ipynb` | Object-Oriented Programming | 12 | **34%** (biggest) |
| 5 | `pcap_05_comprehensions_lambdas_closures_io.ipynb` | Miscellaneous (comprehensions, lambdas, closures, I/O) | 9 | 22% |

## Scope note (added 2026-07-11, second pass)

Javier compared the notebooks against the two official free prep courses on Cisco NetAcad: [Python Essentials 1](https://www.netacad.com/courses/python-essentials-1) (PCEP prep) and [Python Essentials 2](https://www.netacad.com/courses/python-essentials-2) (PCAP prep). Findings:

- **PE1 (PCEP)** covers Lists/List Processing (its Module 3) and Tuples/Dictionaries (its Module 4) — this is prerequisite material PCAP assumes you already know, which is why the original 5 notebooks (scoped strictly to the PCAP-31-03 exam syllabus) didn't include it.
- **PE2 (PCAP prep)** Module 1–4 map almost exactly to the official exam's 5 sections, confirming notebooks 1–5 are correctly scoped — **except** PE2's Module 2 is literally titled "Strings, **String and List Methods**, Exceptions," meaning the real PCAP prep course does pair list methods with string methods even though the terse exam-syllabus text only lists string-specific items.

Resolution (first pass): added a single prerequisites notebook (lists, tuples, dictionaries, nesting) and a new §3.4 in `pcap_03_strings.ipynb` (list methods in parallel with string methods, mirroring PE2 Module 2 exactly).

## Scope note (added 2026-07-17, third pass — full PCEP closure)

Javier kept finding gaps one at a time (control-flow — `if`/`for`/`while` — was nowhere; most of PE1's fundamentals and functions content was missing too) and asked for a single complete review of the entire PCEP-30-02 syllabus before any more building, rather than patching reactively. Fetched the full official PCEP-30-02 syllabus (4 blocks, 30 sub-items total) and rebuilt the prerequisite material as **four notebooks that mirror the official PCEP blocks exactly** (`pcep_01`–`pcep_04`, renamed 2026-07-18 from the original `00a`–`00d` filenames), replacing the old single prerequisites notebook:

- `pcep_01_fundamentals.ipynb` — Block 1: interpreting vs. compiling, keywords, indentation, comments, literals, variables, numeral systems (binary/octal/hex), operators incl. bitwise, floating-point pitfalls, `print()`/`input()`.
- `pcep_02_control_flow.ipynb` — Block 2: `if`/`elif`/`else`, `while`/`for`/`range()`, `break`/`continue`/`pass`, the `for`-`else`/`while`-`else` pattern.
- `pcep_03_data_collections.ipynb` — Block 3: supersedes the old prerequisites notebook; lists (incl. comprehensions, matrices, the copy-vs-clone trap), tuples, dictionaries, strings (cross-references `pcap_03_strings.ipynb` for PCAP-level depth).
- `pcep_04_functions_and_exceptions.ipynb` — Block 4: functions, `return`, recursion, generators (`yield`), parameter passing, scope/`global`, exception hierarchy taxonomy, `try`/`except` ordering.

This closes every remaining gap against both the PCEP-30-02 and PCAP-31-03 official syllabi — no more known missing topics. `00_prerequisites_lists_tuples_dicts.ipynb` was deleted (fully superseded by `pcep_01`–`pcep_04`).

## Filename rename (2026-07-18)

Javier said he was losing track of which files belonged to which source once four tracks (PCEP, PCAP, ATBS, Effective Python) shared one folder. Renamed the PCEP/PCAP notebooks to match the `<prefix>_<NN>_<description>.ipynb` convention already used by `atbs_*` and `ep_*`:

| Old filename | New filename |
|---|---|
| `00a_pcep_fundamentals.ipynb` | `pcep_01_fundamentals.ipynb` |
| `00b_pcep_control_flow.ipynb` | `pcep_02_control_flow.ipynb` |
| `00c_pcep_data_collections.ipynb` | `pcep_03_data_collections.ipynb` |
| `00d_pcep_functions_and_exceptions.ipynb` | `pcep_04_functions_and_exceptions.ipynb` |
| `01_modules_and_packages.ipynb` | `pcap_01_modules_and_packages.ipynb` |
| `02_exceptions.ipynb` | `pcap_02_exceptions.ipynb` |
| `03_strings.ipynb` | `pcap_03_strings.ipynb` |
| `04_oop.ipynb` | `pcap_04_oop.ipynb` |
| `05_comprehensions_lambdas_closures_io.ipynb` | `pcap_05_comprehensions_lambdas_closures_io.ipynb` |

Content is unchanged — only filenames moved. Old files were removed after confirming the new copies were byte-for-byte identical.

## Content checklist

Each subsection below is tagged with its official objective number (PCEP-30-02 for 00a–00d, PCAP-31-03 for 1–5). All are filled in with real explanation + runnable, execution-verified example code.

### PCEP 1. Block 1 — Computer Programming and Python Fundamentals (18%)
- [x] 1.1 Interpreting vs. compiling, lexis/syntax/semantics
- [x] 1.2 Keywords (`keyword.kwlist`), indentation, comments
- [x] 1.3 Literals, variables, numeral systems (binary `0b`, octal `0o`, hex `0x`, `bin()`/`oct()`/`hex()`), PEP-8 naming
- [x] 1.4 Operators — numeric, string, bitwise (`& | ^ ~ << >>`), boolean, relational, precedence; floating-point accuracy trap (`0.1 + 0.2 != 0.3`); type casting
- [x] 1.5 I/O — `print(sep=, end=)`, `input()` always returns `str`

### PCEP 2. Block 2 — Control Flow (29%, heaviest)
- [x] 2.1 `if`/`elif`/`else`, nesting conditionals
- [x] 2.2 `while`/`for`/`range()`, `pass`/`break`/`continue`, the `for`-`else`/`while`-`else` pattern (loop completes without `break`)

### PCEP 3. Block 3 — Data Collections (25%) — supersedes old prerequisites notebook
- [x] 3.1 Lists (indexing, slicing, methods, comprehensions, matrices/nested lists, copy-vs-clone trap: `b = a` vs `a.copy()`)
- [x] 3.2 Tuples (immutability, unpacking)
- [x] 3.3 Dictionaries (access, `get`, `update`, `pop`, `.items()`)
- [x] 3.4 Strings (lighter PCEP-level pass; full depth in `pcap_03_strings.ipynb`)

### PCEP 4. Block 4 — Functions and Exceptions (28%)
- [x] 4.1 Functions, `return`, `None`, recursion (factorial), generators (`yield`/`next()`)
- [x] 4.2 Positional/keyword/default args, scope, `global` vs. shadowing
- [x] 4.3 Exception hierarchy taxonomy (`.__bases__`, `issubclass()`, catching via parent class)
- [x] 4.4 `try`/`except` ordering and propagation

### 1. Modules and Packages (12%)
- [x] 1.1 Import and use modules and packages (`import`, `from…import`, `import as`, `from…import *`, `dir()`, `sys.path`) + advanced qualifying for nested modules (`xml.etree.ElementTree`)
- [x] 1.2 `math` module (`ceil`, `floor`, `trunc`, `factorial`, `hypot`, `sqrt`) — includes the floor()-vs-trunc()-on-negatives exam trap
- [x] 1.3 `random` module (`random()`, `seed()`, `choice()`, `sample()`)
- [x] 1.4 `platform` module (`platform()`, `machine()`, `processor()`, `system()`, `version()`, `python_implementation()`, `python_version_tuple()`)
- [x] 1.5 User-defined modules and packages (`__pycache__`, `__name__`, public/private vars, `__init__.py`) — demonstrated by writing/importing a real module file on disk, **plus** a real nested package tree (`demo_mypkg/utils/helpers.py` with two `__init__.py` files) to cover "searching for/through modules/packages" and "nested packages vs. directory trees" (added 2026-07-18)

### 2. Exceptions (14%)
- [x] 2.1 `try`/`except`/`else`/`finally`, exception hierarchy and ordering, `raise`, `assert`, `args`, **plus** grouped exceptions (`ExceptionGroup`/`except*`, Python 3.11+ — added 2026-07-18, see verification note below)
- [x] 2.2 Custom exceptions (defining, attaching extra data, catching via base class)

### 3. Strings (18%)
- [x] 3.1 Character encoding (ASCII, Unicode, UTF-8, code points, escape sequences)
- [x] 3.2 String operations (`ord()`, `chr()`, indexing, slicing, immutability, iteration, `in`/`not in`) — includes the `'Z' < 'a'` comparison trap
- [x] 3.3 Built-in string methods (`.isxxx()`, `.join()`, `.split()`, `.strip()`, `.find()` vs `.index()`, `sorted()`)
- [x] 3.4 List methods alongside string methods (shared sequence protocol vs. mutability divide — mirrors PE2 Module 2, see scope note above)

### 4. Object-Oriented Programming (34%)
- [x] 4.1 OOP fundamentals (class, object, encapsulation, inheritance, super/subclass)
- [x] 4.2 Class/object properties (instance vs class vars, mutable-class-variable trap, `__dict__`, name mangling)
- [x] 4.3 Methods and `self`
- [x] 4.4 Introspection (`hasattr()`, `__name__`, `__module__`, `__bases__`)
- [x] 4.5 Inheritance (single/multiple, `isinstance()`, overriding, `is`/`is not`, polymorphism, `__str__()`, diamond problem + real `__mro__` output)
- [x] 4.6 Constructors (`__init__`, `super().__init__()`)

### 5. Miscellaneous (22%)
- [x] 5.1 List comprehensions (conditions, nesting)
- [x] 5.2 Lambdas, `map()`, `filter()`
- [x] 5.3 Closures (with `__closure__` proof of captured state)
- [x] 5.4 I/O terminology (streams, handles, text vs binary mode, stdout/stderr)
- [x] 5.5 File I/O (`open()`, `errno`, `.read()`/`.write()`/`.readline()`/`.readlines()`, `bytearray` buffers)

## Verification done
**2026-07-11:** all 5 PCAP notebooks executed end-to-end with `nbconvert --execute`; outputs spot-checked against the explanation text (e.g. confirmed `math.floor(-4.5) == -5` vs `math.trunc(-4.5) == -4`, confirmed the diamond-inheritance `__mro__` order, confirmed name mangling produces `_Account__balance`, confirmed `errno.ENOENT` on `FileNotFoundError`).

**2026-07-17:** all 4 new PCEP notebooks (00a–00d) executed end-to-end with `nbconvert --execute`; outputs spot-checked (e.g. confirmed `for`-`else` only fires when no `break` occurred, confirmed `a.copy()` vs. plain assignment aliasing on lists, confirmed `issubclass(IndexError, LookupError)`, confirmed `global` vs. local shadowing behavior).

**2026-07-18 — full PCAP re-audit + gap fixes:** Javier asked for a full review of the 5 PCAP notebooks against the (re-fetched, still current as of March 2022) official syllabus. 37/40 items were already fully covered; found and fixed 3 gaps:
- 1.1 nested module qualifying — added `xml.etree.ElementTree` dotted-path example, executed and verified (confirmed `xml.fromstring(...)` raises `AttributeError` since only the qualified path works).
- 1.5 package trees — added a real two-level package (`demo_mypkg/utils/helpers.py`, two `__init__.py` files), executed and verified `sys.path` search resolves the nested import correctly.
- 2.1 grouped exceptions (`ExceptionGroup`/`except*`) — **cannot be execution-verified in this sandbox**, which runs Python 3.10 and can't parse `except*` (hard syntax error, introduced in 3.11 via PEP 654). The cell builds the snippet as a string, attempts `exec()`, catches the resulting `SyntaxError`, and prints the code for Javier to run himself on a 3.11+ interpreter (check with `python3 --version` in Cursor). Content correctness cross-checked against PEP 654 and docs.python.org's exception-groups documentation from training knowledge, not live-executed — flag this to Javier if the printed syntax ever looks off.

## Working conventions
- All content in English.
- One notebook = one official section; markdown headers use the official numbering (e.g. `### 4.5 Build a class hierarchy using inheritance`) so progress here maps 1:1.
- Each subsection: real explanation (grounded in docs.python.org, not just the syllabus one-liner) + at least one runnable, verified example cell. No TODO placeholders — see philosophy note above.
