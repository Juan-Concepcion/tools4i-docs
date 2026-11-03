---
title: Native Query Info
layout: default
parent: Database
nav_order: 2
permalink: /tools/native-query-info/
---

# Native Query Info
{: .no_toc }

Everything a `*QRYDFN` holds, in four tabs, including the SQL that does the same thing.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Native Query Info**. Give it the library and
the name, and press **Get Info**.

## The four tabs

| Tab | What it holds |
|---|---|
| **Attributes** | What the query is and how it is set up: type, owner, dates and options |
| **Files** | The files the query reads, each showing **whether its definition still matches** the one the query was built against |
| **Definition** | The query itself: the fields selected, the record selection, the sort and the joins |
| **SQL equivalent** | The same query written as SQL |

Each tab has a **Filter** box that shows only the attributes, files or parts of the
definition containing the text.

## The Files tab is the one that matters first

A query definition breaks quietly when a file changes, and this tab says whether this
one already has. If it has, the report somebody receives by mail has stopped arriving,
or is about to.

**Native Query Level Check** opens the analyzer for this query's whole library, to see
every query in the same situation rather than this one alone.

## Reading the definition

**Expand all** and **Collapse all** open and close every section, which is how a long
definition becomes readable: collapse everything, then open the one section you care
about.

## The SQL equivalent

This is the migration path. When a query has to become something a modern tool can
run, a report, a view, a job somebody schedules elsewhere, the fourth tab is the
starting point instead of a reconstruction by hand. **Copy SQL** puts it on the
clipboard.

## Keeping it

**Save** writes the whole thing as a snapshot and **Open...** brings one back.

## Related

- [Native Query Level Check Analyzer]({{ site.baseurl }}/tools/native-query-level-check-analyzer/)
