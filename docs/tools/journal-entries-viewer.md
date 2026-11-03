---
title: Journal Entries Viewer
layout: default
parent: Database
nav_order: 3
permalink: /tools/journal-entries-viewer/
---

# Journal Entries Viewer
{: .no_toc }

Journal entries with each record image decoded into the file's own columns, and the
before and after images of every update side by side.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Journal Entries Viewer**.

| Field | What it takes |
|---|---|
| **Library** and **Name** | The journaled object |
| **Object type** | `*FILE`, `*DTAARA` or `*DTAQ` |
| **Member** | `*ALL`, `*FIRST` or a name, for a `*FILE`. Ignored for the other types |

## Narrowing the read, before you press Load

A journal receiver holds everything that happened, so the four limits below are not
optional in practice. They decide whether the read takes two seconds or ten minutes.

| Limit | What it does |
|---|---|
| **From** and **To** | Only entries in that window. Leave both empty to read from the start of the receiver chain, which on a busy file is rarely what you want |
| **Entry types** | Separated by spaces: `PT` for an added record, `UP` for an update, `DL` for a delete. Empty means every type |
| **Limit** | Stops after this many entries, up to 1,000,000. 5000 by default |

**Load** reads the entries and decodes each record image into the file's columns. A
read that is taking too long can be stopped with **Cancel**, keeping whatever has come
back.

## The result

Timestamp, operation, entry type, user, job and program, the **relative record
number**, and then the record image decoded into the file's own columns.

The record number is the one to note when you are following a single row through a
day: it stays the same across the write, the updates and the delete, while everything
else about the entry changes.

An **update** is two images, before and after, shown side by side. The changed value
is the one that differs, which sounds obvious until you have tried to find it in two
blocks of raw record data.

The **Filter** box shows only the entries containing the text. It filters what is
already loaded and does not read the journal again.

## From here

**Export** writes the entries shown, with the filters applied, to CSV.

**File Viewer** opens the same object, so you can compare what the journal recorded
with what the file holds today.

## Related

- [File Viewer]({{ site.baseurl }}/tools/file-viewer/)
