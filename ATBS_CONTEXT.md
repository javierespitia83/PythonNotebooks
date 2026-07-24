# PythonNotebooks — Automate the Boring Stuff Review Context

**Goal:** review Python for practical automation skills, following *Automate the Boring Stuff with Python* by Al Sweigart. Unlike the PCAP track, the priority here is **reading fluency**, not exam prep or writing-from-scratch: each notebook pairs a short explanation with real, already-written, runnable code you execute and read in Cursor.

**Edition used:** 3rd edition (2024), the current edition at [automatetheboringstuff.com/3e](https://automatetheboringstuff.com/3e/). It has 24 chapters (the older 2nd edition had 19) — new material includes Google Sheets, SQLite, command-line program design, OCR, and text-to-speech/speech recognition.

**Scope:** full book, both Part I (fundamentals, chapters 1–8) and Part II (automation projects, chapters 9–24), one notebook per chapter.

## Chapter → notebook mapping

| # | Notebook | Chapter | Needs beyond stdlib |
|---|----------|---------|----------------------|
| 1 | `atbs_01_python_basics.ipynb` | Python Basics | — |
| 2 | `atbs_02_if_else_flow_control.ipynb` | if-else and Flow Control | — |
| 3 | `atbs_03_loops.ipynb` | Loops | — |
| 4 | `atbs_04_functions.ipynb` | Functions | — |
| 5 | `atbs_05_debugging.ipynb` | Debugging | — |
| 6 | `atbs_06_lists.ipynb` | Lists | — |
| 7 | `atbs_07_dictionaries.ipynb` | Dictionaries and Structuring Data | — |
| 8 | `atbs_08_strings_text.ipynb` | Strings and Text Editing | `pip install pyperclip` (§8.6) |
| 9 | `atbs_09_regular_expressions.ipynb` | Text Pattern Matching with Regular Expressions | `pip install Humre` (§9.6; `re` itself is stdlib) |
| 10 | `atbs_10_reading_writing_files.ipynb` | Reading and Writing Files | — |
| 11 | `atbs_11_organizing_files.ipynb` | Organizing Files | `pip install Send2Trash` (§11.5) |
| 12 | `atbs_12_cli_programs.ipynb` | Designing and Deploying CLI Programs | `pip install pyinstaller Bext PyMsgBox` (§12.5-12.8; `venv` is stdlib) |
| 13 | `atbs_13_web_scraping.ipynb` | Web Scraping | `pip install requests beautifulsoup4 selenium playwright` (`webbrowser` is stdlib) |
| 14 | `atbs_14_excel_spreadsheets.ipynb` | Excel Spreadsheets | `pip install openpyxl` |
| 15 | `atbs_15_google_sheets.ipynb` | Google Sheets | `pip install ezsheets` + Google OAuth credentials (conceptual notebook, not runnable without your own setup) |
| 16 | `atbs_16_sqlite_databases.ipynb` | SQLite Databases | — (`sqlite3` is stdlib) |
| 17 | `atbs_17_pdf_word.ipynb` | PDF and Word Documents | `pip install pypdf python-docx pdfminer.six` |
| 18 | `atbs_18_csv_json_xml.ipynb` | CSV, JSON, and XML Files | — |
| 19 | `atbs_19_time_scheduling.ipynb` | Time, Scheduling Tasks, Launching Programs | — (optional `pip install schedule`) |
| 20 | `atbs_20_email_texts.ipynb` | Sending Email, Texts, Push Notifications | `pip install ezgmail` + Google OAuth (send/read Gmail); `requests` for ntfy/Twilio — reference code, real credentials needed |
| 21 | `atbs_21_graphs_images.ipynb` | Making Graphs and Manipulating Images | `pip install pillow matplotlib pyperclipimg` |
| 22 | `atbs_22_ocr.ipynb` | Recognizing Text in Images | Tesseract OCR engine (system install) + `pip install pytesseract`; NAPS2 app for §22.4 |
| 23 | `atbs_23_keyboard_mouse.ipynb` | Controlling the Keyboard and Mouse | `pip install pyautogui` — controls your real mouse/keyboard, read-only recommended |
| 24 | `atbs_24_tts_speech.ipynb` | Text-to-Speech and Speech Recognition | `pip install pyttsx3 openai-whisper yt-dlp` (+ ffmpeg for Whisper) |

## Verification done (2026-07-11)
All 24 notebooks were executed end-to-end with `nbconvert --execute` in a sandbox with `requests`, `beautifulsoup4`, `openpyxl`, `python-docx`, `pillow`, and `matplotlib` installed. Every runnable code cell executed successfully except chapter 1's `input()` call, which needs a human typing in an interactive kernel (expected — works normally in Cursor). Chapters 15, 20, 22, 23, 24 intentionally keep their external-service/hardware-dependent code commented out with a short illustrative `print()` standing in, since they need credentials, OS-level installs, or real hardware (mic/OCR engine) that can't be verified generically.

## 2026-07-18 — full re-audit against the live book site, 13 chapters patched

Javier asked to confirm all 24 chapters still match the current online edition (automatetheboringstuff.com/3e). Fetched every chapter page fresh and diffed against the notebooks. 11 chapters (1–7, 10, 15, 18, 19) had no gaps. 13 chapters were missing named libraries/techniques the live book covers — mostly newer tools folded into this edition over time. Fixed all 13:

| Chapter | Added | Executable here? |
|---|---|---|
| 8 | `pyperclip` (clipboard copy/paste, §8.6) | Text-transform logic yes; clipboard I/O no (headless, caught via `try/except`) |
| 9 | `Humre` (human-readable regex builder, §9.6) | Yes, fully |
| 11 | `send2trash` (recoverable delete, §11.5) | No — sandbox permission error (caught); works on a real desktop |
| 12 | `PyInstaller` (§12.5), `venv` (§12.6), `Bext` (§12.7), `PyMsgBox` (§12.8) | PyInstaller/venv/Bext yes, fully; PyMsgBox no (needs Tkinter/display, caught) |
| 13 | `Selenium` (§13.5), `Playwright` (§13.6), `webbrowser` (§13.7) | No for Selenium/Playwright (no browser binaries/root in sandbox) — illustrative, correct code only; `webbrowser` yes (returns `False` headless, doesn't error) |
| 14 | `openpyxl` charts — Bar/Line/Pie/Scatter (§14.5) | Yes, fully |
| 16 | Foreign keys + `INNER JOIN` across tables (§16.5) | Yes, fully |
| 17 | `PdfMiner` alt extractor (§17.1b), PDF encrypt/decrypt (§17.4), image extraction (§17.5) | Yes, fully (built real demo PDFs with `reportlab`) |
| 20 | **Replaced** outdated `imapclient`/`pyzmail` (§20.2) with `EZGmail`, which is what the book's current edition actually uses for both sending and reading Gmail; made §20.3 concrete with a real `ntfy.sh` push-notification call | EZGmail no (needs OAuth credentials, illustrative); ntfy code is real and correct but this sandbox's network can't reach ntfy.sh (caught) |
| 21 | `pyperclipimg` (image clipboard, §21.5) | No — same headless clipboard limit as ch.8 (caught) |
| 22 | `NAPS2` via `subprocess` (searchable-PDF scanning, §22.4) | No — external desktop app not installable here (checked via `shutil.which`, falls back to illustrative) |
| 23 | Image recognition `locateOnScreen()` (§23.5), window management `getActiveWindow()` (§23.6) | No — needs a real screen/display (caught) |
| 24 | `yt-dlp` (§24.4), paired with Whisper for auto-transcription | No — sandbox network can't reach YouTube (caught); code is real and correct |

**Verification methodology:** every new library was test-installed and probed for headless-runnability *before* writing content, so each addition either runs for real (PyInstaller actually compiles and runs a binary; openpyxl chart round-trips through a saved `.xlsx`; PdfMiner/pypdf build and read real demo PDFs with `reportlab`) or fails in a caught, explained way consistent with the existing convention for OS/hardware/credential-dependent chapters. No content was written as untested guesswork.

## Working conventions
- English only, reading-first: explanations are short, code is complete and pre-written (not TODO placeholders) — run it, then modify a value and re-run to build intuition.
- One notebook = one official book chapter; markdown headers use the book's own numbering (e.g. `### 9.3 Quantifiers`) for easy cross-reference back to the source text online.
- Chapters needing installs list the exact `pip install` in a setup note at the top of the notebook.
- When a chapter's real content depends on a network service, external app, or display/clipboard/credentials unavailable in a given environment, the code is still the real, correct API — wrapped in `try/except` so the notebook still runs cleanly end-to-end, with a note on what happens on a normal desktop.
