---
title: Object and Sources
layout: default
parent: Object references
nav_order: 6
permalink: /tools/object-and-sources/
---

# Object and Sources
{: .no_toc }

Source members against compiled objects, across libraries: what has no source, what
has no object, and what is stale.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## What it is for

Before any large rebuild, one question has to be answered: is the source you are about
to compile the source the object was built from. When it is not, a recompilation
quietly reverts a fix nobody promoted.

## Opening it

**Tools4i** in the Activity Bar, then **Object and Sources**.

| Field | What it takes |
|---|---|
| **Libraries** | Which to compare. Spaces or commas, `*` for a group. **Left empty, the user part of the job's library list is analyzed** |
| **Source files** | Which source files to read members from, such as `QRPGLESRC`. `Q*` by default. Narrowing it makes the read faster |

**Analyze** reads both sides and matches them up; several libraries take a while.
**Cancel** stops it and keeps whatever has been read.

## The four tabs

| Tab | What it shows |
|---|---|
| **Sources** | Every source member with the object of the same name, or the fact that there is none |
| **Objects** | The reverse: every object with the source it was built from, or the fact that none was found |
| **Skipped Sources** | Members left out by the skip rules. **Check here when something you expected is missing** |
| **Skipped Objects** | Objects left out, either by the rules or because their type is never built from source |

The two skipped tabs are what make the result trustworthy. A tool that silently drops
rows cannot be checked; this one says what it dropped and why.

## The skip rules

Every shop has pairs that are supposed to look mismatched. The rules keep the real
findings from being buried under the normal ones:

| Rule | What it skips | Typical value |
|---|---|---|
| **Name patterns** | `LIBRARY/FILE/MEMBER` patterns, comma-separated, `*` anywhere. A two-part pattern assumes any library | `*/QSRVSRC/*P, */QTESTSRC/*` |
| **Description** | A member whose description contains any of these words | `copybook, template` |
| **Source type** | Types that never produce an object of their own | `*INC, *CPY, TXT` |
| **Object type** | Object types to leave out. They are still listed under Skipped Objects | `*FILE, *CMD, *DTAARA` |
| **Object owner** | Profiles whose objects to skip, handy for leaving out IBM-supplied objects | `QSYS, QPGMR` |

There is also a switch for objects whose source lives **outside** the libraries being
analyzed, which is the normal case for a shop that keeps sources and objects apart.

## Keeping it

**Save** writes the result as a snapshot and **Open...** brings it back, which is how
the same reconciliation is compared before and after a promotion.

## Related

- [Library Compile Order]({{ site.baseurl }}/tools/library-compile-order/)
- [Sync Server Library]({{ site.baseurl }}/tools/sync-server-library/)
