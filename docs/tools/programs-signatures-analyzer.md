---
title: Programs Signatures Analyzer
layout: default
parent: Object references
nav_order: 7
permalink: /tools/programs-signatures-analyzer/
---

# Programs Signatures Analyzer
{: .no_toc }

The callers that will fail at activation because the service program they were bound
to no longer carries the signature they hold.
{: .fs-5 .fw-300 }

This tool is in **beta**. It is usable and in daily use, and its results should be
reviewed before you act on them rather than taken as a complete list.
{: .label .label-yellow }

## Why this failure is special

It does not happen at compile time, and it does not happen when the program starts.
It happens at **activation**: in production, at the moment a program first calls into
the service program, long after everybody agreed the change was finished.

## Opening it

**Tools4i** in the Activity Bar, then **Programs Signatures Analyzer**.

| Field | What it takes |
|---|---|
| **Caller libraries** | The libraries holding the programs and service programs to check, in the order entered |
| **Service program libraries** | The libraries holding the service programs those callers are bound to, whose **current** signatures they are checked against. Empty means the library list |
| **Include system** | Also checks the ones supplied by IBM, which are usually noise |

**Analyze** compares the signature each caller was bound with against the signatures
its service program carries now. **Cancel** stops it, reporting nothing.

## Comparison

Every caller-and-service-program pair, with **the bound signature beside the current
ones** and the verdict. Its **filter** narrows across caller, service program,
signature and status.

**Affected only** hides the pairs that still match, **hide system** drops the
IBM-supplied ones, and **Export** writes the rows shown to CSV.

## Callers to Rebind

The distinct callers that will fail, one line each whatever the number of service
programs behind them. Its **filter** narrows by caller or library name, **Copy list**
puts the `LIBRARY/PROGRAM` list on the clipboard, and it exports to CSV.

## Service Programs

Which ones have moved on from the signature their callers hold, and how many each one
breaks, with its own filter and export.

The third tab is the one that finds the cause rather than the symptom: twenty callers
failing usually means one service program was rebuilt with a changed export list.

## Acting on a row

**Open Source (read only)** opens the caller's source, and **Copy Caller Name**,
**Copy Service Program Name** and **Name and Library** put the names where a rebind
command can use them.

## What to do with it

Rebind the callers, or restore the signature. Both are valid. The point of the list is
that the decision is made before the activation failure, not after it.

**Copy list** puts the `LIBRARY/PROGRAM` list on the clipboard, every tab exports to
CSV, and **Save** keeps the result as a snapshot.

## Related

- [Binding Directory Sync]({{ site.baseurl }}/tools/binding-directory-sync/)
- [Procedure Change Impact Analysis]({{ site.baseurl }}/tools/procedure-change-impact-analysis/)
