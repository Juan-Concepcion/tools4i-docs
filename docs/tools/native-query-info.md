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

## Attributes

What the query is and how it is set up: its type, its owner, its dates and its
options. The **Filter** box shows only the attributes whose name or value contains the
text.

## Files

The files the query reads, each showing **whether its definition still matches** the
one the query was built against. Its own **Filter** box narrows the list.

This is the tab that matters first: a query definition breaks quietly when a file
changes, and this tab says whether this one already has. If it has, the report
somebody receives by mail has stopped arriving, or is about to.

The right-click menu on a file row goes where the question usually goes next:
**File Viewer** for its data, **Object Change Impact Analysis** for what a change to
it would break, **Reveal in Navigate**, and **Add library to library list** for the
library that file lives in.

**Native Query Level Check** opens the analyzer for this query's whole library, to see
every query in the same situation rather than this one alone.

## Definition

The query itself: the fields selected, the record selection, the sort and the joins.

**Expand all** and **Collapse all** open and close every section, which is how a long
definition becomes readable: collapse everything, then open the one section you care
about. The **Filter** box shows only the parts containing the text.

## SQL equivalent

The same query written as SQL, with **Copy SQL** to take it away.

This is the migration path. When a query has to become something a modern tool can
run, a report, a view, a job somebody schedules elsewhere, the fourth tab is the
starting point instead of a reconstruction by hand.

## Keeping it

**Save** writes the whole thing as a snapshot and **Open...** brings one back.

## Related

- [Native Query Level Check Analyzer]({{ site.baseurl }}/tools/native-query-level-check-analyzer/)
