---
title: Sources Scan Results
layout: default
parent: Search
nav_order: 3
permalink: /tools/sources-scan-results/
---

# Sources Scan Results
{: .no_toc }

Every scan keeps its own tab, with the members on one side and the matching statements
on the other, and the options that decide which of the hits are worth reading.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

It opens by itself when a scan finishes. To get back to it later, **Tools4i** in the
Activity Bar, then **Sources Scan Results**.

Closing a tab does not undo the scan, but it does lose it. Save it first if you want
to keep it.

## The four options above the result

| Option | What it does |
|---|---|
| **Keep matches in commented-out code** | On by default. Switch it **off** to see only the lines that actually run. On an old code base this is the single biggest improvement to a result |
| **First match only** | When the same member name appears in several libraries, keeps only the copy from the highest-priority one |
| **Highlight duplicates** | Marks the copies that First match only would drop, so you can see what is being hidden before you switch it on |
| **Quick filters** | The one-line boxes under each column heading |

Use **Highlight duplicates** before **First match only**, not after. Seeing which copy
is about to be discarded is the point.

## Library priority

**Library priority** opens the ranked list, with arrows to move a library **up** and
**down**. The one at the top wins when the same member is found in several.

Set it to the order your library list uses at run time, and the result answers "which
copy of this program actually runs", which is a different question from "where does
this program exist".

## The columns

Library, File, Member, Type, Description, and for a local scan the subfolder. They
sort, and the quick filters narrow them.

## The right-click menu

### On a result row

| Entry | |
|---|---|
| **Open** | In the mode the radio above says, read-only or edit |
| **Remove from results** | Takes the row out of this tab only |
| **Copy member...** | To another library or source file |
| **Copy to Library...** | |
| **Download...** | **Member**, **File to Member** or **Library to File to Member** |
| **Copy Name**, **Copy Name and Location**, **Copy Path** | |
| **Select for Compare**, then **Compare with** | The same five choices as the browser |

With several rows selected, **Copy Names** replaces the single-name entries.

### On the tab itself

| Entry | |
|---|---|
| **Load in Scan Sources** | Puts the criteria that produced this tab back into Scan Server Sources or Scan Local Sources |
| **Copy Search Parameters** | The same criteria as text, which is how a search travels into a ticket |
| **Save...** | The tab as a snapshot |
| **Export...** | To CSV |

Copying the parameters is worth the habit: whoever reads the ticket reproduces exactly
what you ran, instead of approximately what you described.

## Keeping a result

**Save** writes the tab as a snapshot, and **Open...** brings one back in a new tab,
with no connection needed. A scan that took twenty minutes over forty libraries is
worth keeping.

## Related

- [Scan Server Sources]({{ site.baseurl }}/tools/scan-server-sources/)
- [Scan Local Sources]({{ site.baseurl }}/tools/scan-local-sources/)
