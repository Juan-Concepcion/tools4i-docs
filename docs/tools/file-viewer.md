---
title: File Viewer
layout: default
parent: Database
nav_order: 5
permalink: /tools/file-viewer/
---

# File Viewer
{: .no_toc }

A file in six tabs: what it is, the records themselves, who is built over it, every
column, a data structure ready to paste, and a layout for a file that describes itself
nowhere.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **File Viewer**.

| Field | What it takes |
|---|---|
| **Library** | Always required |
| **File** | A physical file, table, logical file, view or index. Always required |
| **Member** | Only for multi-member physical files: `*FIRST`, `*ALL`, or a name. Leave `*FIRST` for tables and single-member files |
| **Format** | The record format, only for multi-format logical files. It fills after Load, then you pick |

**Load** reads the file. **Only the Info tab loads now**; each other tab is fetched the
first time you open it, so opening a file costs one read rather than six.

Every tab has its own **Refresh**, and most have **Reset quick filters** and
**Export** to CSV.

## Info

What the file is: type, members, record length, key and journaling. The **Filter** box
shows only the attributes whose name or value contains what you type.

**Actions** carries the things to do with the file itself, and the right-click menu on
a row offers **Navigate to Object** or **to Source**, **Journal entries**, **Object
Change Impact** and **Open Source**.

## Data

The records, read straight from the file.

| Control | What it does |
|---|---|
| **Limit** | Stops after this many rows, up to 1,000,000. 5000 by default; a smaller number returns faster |
| **Filter** box | Shows only the records containing the text in any column. It filters **what is already loaded** and does not read the file again |
| Quick filters, per column | The same, column by column |
| **SQL Where** | Re-reads the file with a `WHERE` clause built on this file's columns. Unlike the filter boxes, **this narrows the read itself** |
| **Long names** | Shows SQL long names instead of short system names |
| **Export** | The records shown, with the filters applied, to CSV |
| **Add row** | Inserts a record. Physical files and tables only |

Double-click a row to edit it: the editor shows every field, **Save** writes the values
back to the record on the server, **Cancel** closes without changing it.

The `WHERE` dialog has a **Find column** box of its own, which matters on a file with
hundreds of columns, and a **Clear** that removes the clause and re-reads.

**Refresh keeps the quick filters you typed and the column you sorted on**, so you can
watch one row change without setting the view up again.

## Dependents

The logical files, views and indexes built over this file, each with its object type,
description and SQL long name.

This answers "who breaks if I change this record format" before the change, instead of
letting the compiler answer it afterwards. The right-click menu opens any of them in
the File Viewer in turn.

## Columns/Fields

Every column with its type, length, decimals and text, filterable and exportable, and
including each field's position in the record.

## RPG Data Structure

A data structure generated from the real definition, ready to paste.

| Option | Choices |
|---|---|
| **Style** | Full free, free, or fixed format |
| **Positions** | With or without |
| **Initialized from** | The data type defaults, or the first record |
| **Name** | A prefix and a postfix, `_ds` by default |
| **Array** | Optionally an array, with the number of leading records to load into it, which is also its number of elements |

**Copy** puts it on the clipboard. **Search** highlights text inside the generated
source.

## Custom fields

Reading a file the way a legacy program reads a **program-described file**: you give
the layout, and the decoded values come back as a normal grid.

| Button | What it does |
|---|---|
| **Add field** | One row: name, position, type, decimals |
| **Input specs** | Imports the layout from fixed-format RPG input specs or a positional data structure, pasted in |
| **Open** / **Save** | Loads or keeps the layout as a local file. Saving changes nothing on the server |
| **Reset** | Clears every definition |
| **Refresh** | Reads the file and decodes the records with the layout |
| **Export** | The decoded rows as CSV |
| **SQL SELECT** | Writes the SQL that returns these same columns, typed, and opens it in a new editor |

Each field row carries its own buttons:

| Button | What it does |
|---|---|
| **‹** and **›** | Move this field one byte left or right. Hold **Shift** for ten |
| **«** and **»** | Move this field **and every row below it** one byte, which is what you want when a field was inserted into the record |
| **↑** and **↓** | Move the row up or down. Hold **Shift** to send it to the top or the bottom |
| **✕** | Remove it. Hold **Shift** to remove it and every row below it |

The type list decides how those positions are read: as text, as a packed or zoned
number, as a date, and so on. A date kept in a numeric field reads as a date, and a
record that does not fit the layout says so in the cell instead of showing a number
assembled from bytes that are not one.

There is a guide for this one:
[A file described by its program]({{ site.baseurl }}/guides/program-described-file/).

## Small things that help

- The note explaining a tab opens from a question mark, instead of standing above the
  work.
- The line between the field definitions and the data can be dragged to give the room
  to whichever of the two you are working on, and a double click puts it back.
- A read that is taking too long can be stopped with **Cancel**, keeping whatever has
  come back so far.

## Related

- [Journal Entries Viewer]({{ site.baseurl }}/tools/journal-entries-viewer/)
- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
