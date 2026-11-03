---
title: Binding Directory Editor
layout: default
parent: Binding directories
nav_order: 1
permalink: /tools/binding-directory-editor/
---

# Binding Directory Editor
{: .no_toc }

A `*BNDDIR` is normally maintained one entry at a time, with no way to see the whole
picture. Here the whole list is on screen at once.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Binding Directory Editor**.

| Button | What it does |
|---|---|
| **Get Info** | Reads the entries from the server, for the library and name you gave |
| **Open** | Opens a previously downloaded `.BINDIR` file, with no connection |
| **Download** | Writes the current entries, with the description, to a local `.BINDIR` file |

The two ways in matter later: **Save** applies to **the server** when the list came
from Get Info, and to **the file** when it came from Open. The panel always knows
which, so the same button never does the unexpected thing.

## The table

| Column | |
|---|---|
| **#** | The order, which is the order the binder searches |
| **Object**, **Type**, **Library** | The entry |
| **Activation** | Immediate or deferred |
| **Created** | |
| **State** | New, changed or removed, for the edits not yet applied |

Every column filters, and the **quick filters** switch on the bar shows or hides that
row of boxes.

## Editing

**Add entry** appends one. Rows are edited in place, and the **State** column marks
what you have done to each.

Nothing reaches the object until **Save**, and **Discard** reverts everything back to
the loaded state, so several edits are committed in a single pass or thrown away
together.

## Does any of it still exist

**Check on the server whether each entry's object exists** does exactly that, entry by
entry.

On a binding directory carried from release to release, this is where the entries
nobody removed finally surface.

## Comparing

**Compare with...** puts this binding directory against another on the server and
shows what is missing, what is extra and what is bound differently. To bring one in
line with the other in a single action, use
[Binding Directory Sync]({{ site.baseurl }}/tools/binding-directory-sync/).

## Why the file matters

A binding directory edited as a `.BINDIR` file can be committed with the rest of a
project and applied back to a library later by
[Upload Local Project]({{ site.baseurl }}/tools/upload-local-project/).

That is how a binding directory gets into source control, where it belongs, instead of
existing only as an object somebody changed once.

## Related

- [Binding Directory Sync]({{ site.baseurl }}/tools/binding-directory-sync/)
- [Programs Signatures Analyzer]({{ site.baseurl }}/tools/programs-signatures-analyzer/)
