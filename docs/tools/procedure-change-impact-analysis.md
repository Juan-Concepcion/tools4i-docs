---
title: Procedure Change Impact Analysis
layout: default
parent: Object references
nav_order: 5
permalink: /tools/procedure-change-impact-analysis/
---

# Procedure Change Impact Analysis
{: .no_toc }

For one exported subprocedure: every module, service program, program and external
stored procedure to rebuild, in a safe order.
{: .fs-5 .fw-300 }

This tool is in **beta**. It is usable and in daily use, and its results should be
reviewed before you act on them rather than taken as a complete list.
{: .label .label-yellow }

## Opening it

**Tools4i** in the Activity Bar, then **Procedure Change Impact Analysis**.

| Field | What it takes |
|---|---|
| **Procedure** | The exported subprocedure whose signature or behavior is about to change. **Give the name as it is exported**, not the source member |
| **Object** | The module or service program that defines it. It is the starting point of the rebuild chain |
| **Libraries** | Searched for whatever binds the procedure. Empty means the current library list |
| **Recursive** | Also lists the programs that call the impacted ones, for review only |

**Analyze** follows the binding chain out from the procedure. **Cancel** stops it,
reporting nothing.

## The result

Everything to rebuild, with the action needed for each, in an order that works. The
filter box narrows across object, library, type and action.

## Confirm in source, and what a miss means

**Confirm in source** reads the source of the objects tied **straight** to the one
that holds the procedure, those that define, export or bind it, and reports which of
them name it. Indirect callers are not read.

Read that result carefully:

> A compiled object cannot say which procedure a caller invokes. **A miss means there
> is no explicit evidence in the source, never proof that the procedure is unused.**

A dynamic call, a name built at run time, or a source that is not where the object
says it is, all produce a miss.

## Taking it out

**Copy plan** puts the ordered rebuild plan on the clipboard, **Export** writes CSV,
and **Save** keeps the plan as a snapshot **including any source confirmation already
run**, so the evidence travels with it.

The row menu offers **Open Source (read only)**, **Copy Name** and **Copy
Library/Object**.

## Related

- [Programs Signatures Analyzer]({{ site.baseurl }}/tools/programs-signatures-analyzer/)
- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
