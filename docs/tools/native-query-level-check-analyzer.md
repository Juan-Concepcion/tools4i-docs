---
title: Native Query Level Check Analyzer
layout: default
parent: Object references
nav_order: 2
permalink: /tools/native-query-level-check-analyzer/
---

# Native Query Level Check Analyzer
{: .no_toc }

The `*QRYDFN` queries that will fail because a file definition changed.
{: .fs-5 .fw-300 }

## Why it has its own tool

Query definitions break for exactly the same reason programs do, and they are
remembered last, because nobody thinks of them as code. They are usually the reports
somebody receives by mail, so the failure arrives as "I did not get my report" a week
after the change.

## Opening it

**Tools4i** in the Activity Bar, then **Native Query Level Check Analyzer**. You can
also reach it for one library from
[Native Query Info]({{ site.baseurl }}/tools/native-query-info/).

| Field | What it takes |
|---|---|
| **Query libraries** | The libraries holding the query definitions. Spaces or commas, `*` allowed, searched in the order entered |
| **Data libraries** | The libraries holding the files those queries read |

**Analyze** compares the level ids stored in each query definition against the files
as they are now. **Cancel** stops it, reporting nothing.

## Comparison

Every query-and-file pair, with both level ids side by side and the verdict. Its
**filter** narrows across query, file, record format and status, **Affected only**
hides the pairs that still match, and **Export** writes the rows shown to CSV.

## Queries Affected

The distinct queries that will fail, one line each. Its **filter** narrows by query or
library name, **Copy list** puts the `LIBRARY/QUERY` list on the clipboard, and
it exports to CSV.

## Files

Which record formats changed, and how many queries each one breaks, with its own
filter and export.

## What to do with the result

A query that fails has to be recreated, or replaced. If it is going to be replaced,
the SQL equivalent in
[Native Query Info]({{ site.baseurl }}/tools/native-query-info/) is the starting
point.

**Copy list** puts the `LIBRARY/QUERY` list on the clipboard, every tab exports to
CSV, and **Save** keeps the result as a snapshot.

## Related

- [Programs Level Check Analyzer]({{ site.baseurl }}/tools/programs-level-check-analyzer/)
- [Native Query Info]({{ site.baseurl }}/tools/native-query-info/)
