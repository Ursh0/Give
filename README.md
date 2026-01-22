# Give (mini submission + testing system)

A lightweight, POSIX-shell reimplementation of a simple course-style
submission and testing workflow. It provides commands to create
assignments, accept multiple student submissions, list/status/fetch
submissions, run autotests, run automarking, and remove assignments ---
all backed by a local `.give/` directory.

Private Repository - Contact me for access

## What it does

-   Stores all state in **`.give/`** (no external storage)
-   Supports **multiple submissions per student** (latest is the one
    marked; older ones remain fetchable)
-   Matches a **reference implementation's** behaviour, including:
    -   exact error messages to **stderr**
    -   exit status **1** on errors

## Commands

-   `give-add <assignment> <solution> <autotests> <automarking>`\
    Create a new assignment and copy spec files into `.give/`.

-   `give-submit <assignment> <zid> <filename>`\
    Record a submission for a student (multiple allowed).

-   `give-summary`\
    List assignments and how many students have submitted.

-   `give-status <zid>`\
    List all submissions made by a student.

-   `give-fetch <assignment> <zid> [n]`\
    Print a submission. Defaults to the last submission.\
    Supports relative indices: `0` = last, `-1` = second-last, etc.

-   `give-autotest <assignment> <filename>`\
    Run the assignment's autotests against a program file.

-   `give-mark <assignment>`\
    Run automarking on the **latest submission** of each student.

-   `give-rm <assignment>`\
    Remove an assignment and associated stored data.

## Autotest / automarking file format

Each test is one line with **pipe-separated columns**:

`label|args|stdin|options` (autotest)\
`label|args|stdin|options|marks` (automarking)

Notes: - `stdin` can include `\n` sequences for newlines - `options` may
include any of: `b c d w` (comparison normalisation flags) - lines
starting with `#` and empty lines are ignored

## Implementation constraints

-   Written in **POSIX shell** (runs with `dash`)
-   Uses only a restricted set of standard Unix utilities
-   No concurrency assumptions (one command runs at a time)

## Repo contents

-   8 executable scripts:
    -   `give-add`, `give-submit`, `give-summary`, `give-status`
    -   `give-fetch`, `give-autotest`, `give-mark`, `give-rm`
-   A small test suite: `test0.sh` ... `test9.sh`
# Give
University Style automated submission testing and workflow, built in POSIX compliant Shell. 
