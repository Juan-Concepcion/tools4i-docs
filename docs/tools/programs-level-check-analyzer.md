---
title: Programs Level Check Analyzer
layout: default
parent: Object references
nav_order: 1
permalink: /tools/programs-level-check-analyzer/
---

# Programs Level Check Analyzer
{: .no_toc }

The programs that will level-check against the files in your data libraries, before a
user finds them.
{: .fs-5 .fw-300 }

For the whole job, read
[What a change would break]({{ site.baseurl }}/guides/change-impact/).
{: .fs-3 }

## Why it matters

A program compiled against an old record format does not fail at compile time. It
fails at run time, in front of somebody, with a level check.

## Opening it

**Tools4i** in the Activity Bar, then **Programs Level Check Analyzer**.

| Field | What it takes |
|---|---|
| **Program libraries** | The libraries holding the programs to check. Spaces or commas, and a name may end in `*`. They are searched **in the order entered**, so the first match wins, exactly as a library list resolves |
| **Data libraries** | The libraries holding the files those programs open, whose **current** definitions the programs are compared against |

**Analyze** compares the record-format level ids compiled into each program against
the files as they are now. **Cancel** stops it before it finishes, and nothing is
reported.

## The three tabs

| Tab | What it shows |
|---|---|
| **Comparison** | Every program-and-file pair examined, with **both level ids side by side** and the verdict for each |
| **Programs to Recompile** | The distinct programs that will fail, one line each whatever the number of files behind them. This is the work list |
| **Files** | The same result from the other side: which record formats changed, and how many programs each one breaks |

Each tab has a filter box of its own, narrowing across program, file, record format
and status.

## Affected only, and the case it reveals

**Affected only** hides the pairs that still match.

It also surfaces the pairs where **level checking is simply turned off**. Those
programs will not fail. They will read the record with the old layout and write
whatever that produces, quietly, for as long as nobody notices. A list of them is
worth more than the list of programs that fail loudly.

## Taking it out

**Copy list** puts the `LIBRARY/PROGRAM` list on the clipboard, and each tab exports
to CSV, so the recompilation becomes a ticket somebody can work through.

**Save** keeps the whole result as a snapshot and **Open...** brings it back, which is
how a before-and-after pair of runs is compared.

## Related

- [Native Query Level Check Analyzer]({{ site.baseurl }}/tools/native-query-level-check-analyzer/)
- [Library Compile Order]({{ site.baseurl }}/tools/library-compile-order/)
