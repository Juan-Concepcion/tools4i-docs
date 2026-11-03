---
title: Sync Server Library
layout: default
parent: Compare and sync
nav_order: 2
permalink: /tools/sync-server-library/
---

# Sync Server Library
{: .no_toc }

A newer project library against one or more base libraries, compared **line by line**,
and classified by what happened to each line.
{: .fs-5 .fw-300 }

## What it is for

Before promoting a project library, the question is not only which members differ. It
is whether the newer copy still contains everything the base had, or whether somebody
started from an old copy and silently dropped a fix that was promoted in the meantime.

## Opening it

**Tools4i** in the Activity Bar, then **Sync Server Library**.

| Field | What it takes |
|---|---|
| **Newer library** | The project library: the up-to-date copy, expected to contain every base member's lines |
| **Source files** | `Q*` by default, wildcards allowed |
| **Base libraries** | Added one at a time with **Add**, into an ordered list |

**The order of the base list matters.** The libraries are searched top to bottom and
the **first match** is used as the base, which is the same rule a library list follows
at run time. Get it wrong and you are comparing against a copy nobody runs, so it is
worth pasting the real library list in rather than typing the two you remember.

**Compare** reads both and matches them member by member. Nothing is copied.

## The seven verdicts

This is the part that makes the tool worth running:

| Verdict | What it means |
|---|---|
| **Identical** | The member is the same |
| **Changed, Base kept** | The newer copy changed the line but the base content is still there |
| **Base code dropped** | The newer copy **lost** lines the base had. This is the one to look at first |
| **Missing in Newer** | The base has a member the project does not |
| **Created in Newer** | New work, with no base counterpart |
| **Re-qualified in Newer** | The same code, moved or re-qualified |
| **Added in Newer, different qualifier** | Added, but not where the base would have it |

**Base code dropped** is the promotion accident this tool exists to catch: a developer
started from an old copy, and promoting it would undo somebody else's fix.

## Reading it

**Only differences** hides the identical members. The **filter** box narrows by name
with wildcards, **quick filters** add a box over each column, and **Expand all** and
**Collapse all** open or close the groups.

The columns say the member, its type, the newer and base sides, which base library the
match came from, and the verdict.

**Navigate to Library** jumps from a row into
[Navigate Server]({{ site.baseurl }}/tools/navigate-server/) on that library.

## Copying members across

Copying the members you picked is done together rather than one at a time, which is
much quicker on a large set, and anything that could not be copied is still named.

A copy that would **replace** members already in the target library says so first,
naming how many and which, so a mistyped library name costs nothing.

## Related

- [Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/)
- [Object and Sources]({{ site.baseurl }}/tools/object-and-sources/)
