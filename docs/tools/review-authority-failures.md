---
title: Review Authority Failures
layout: default
parent: Users
nav_order: 2
permalink: /tools/review-authority-failures/
---

# Review Authority Failures
{: .no_toc }

The authorization failures the security audit journal recorded, over a window you
choose, with the routine noise taken out.
{: .fs-5 .fw-300 }

## What it is for

Two questions, and they are opposites. "Why was this user refused" is the support one.
"Who has been trying things they should not" is the security one. Both are answered by
the same entries.

## Opening it

**Tools4i** in the Activity Bar, then **Review Authority Failures**.

| Control | What it does |
|---|---|
| **From** and **To** | The range. Blank at the end means now |
| **Last 24h** | Puts the range back to the last day |
| **Exclude** | Hides entries whose current user is one of these: the server profiles that fail authority checks routinely. Comma-separated |
| **Limit** | Returns at most this many of the newest entries, up to 1,000,000. 2000 by default |
| **All columns** | Shows every field the journal entry carries, not just the usual ones |

One thing worth knowing about the limit: **it caps what comes back, not how long the
journal takes to read**. To make the read itself faster, narrow the dates.

**Load** reads the entries; **Cancel** stops it, reporting nothing.

## Drilling in

From a failure, you can open the authorities actually held on the object that refused
the access. That is the step that turns "access denied" into a sentence you can act
on: the profile holds this, the object requires that.

The row menu also jumps to the context around the failure:

- **User info** for the profile,
- **Job info** and **Job log** for the job it happened in,
- **Object Change Impact** for the object involved,
- **Reveal in Navigate**, to see the object in its library.

## Taking it out

The **Filter** box narrows across every column, and **Export** writes the rows shown
to CSV with the search and sort applied.

## What it cannot show

If the system is not auditing authority failures, there is nothing here to read. An
empty result is not the same as no failures.

## Related

- [User Info]({{ site.baseurl }}/tools/user-info/)
