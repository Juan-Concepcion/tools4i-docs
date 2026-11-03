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
| **Format** | The record format, only for multi-format logical files. It stays disabled otherwise, fills after Load, and then you pick |

**Load** reads the file. **Only the Info tab loads now**; each other tab is fetched the
first time you open it, so opening a file costs one read rather than six.

---

## Info

What the file is: its type, its members, the record length, the key and whether it is
journaled.

| Control | What it does |
|---|---|
| **Refresh** | Reads it again |
| **Filter** | Shows only the attributes whose name or value contains the text |
| **Actions** | The things to do with the file itself, gathered in one menu |

**The right-click menu** on an attribute row: **Navigate to Source** or **to Object**,
**Journal entries**, **Object Change Impact** and **Open Source**.

---

## Data

The records, read straight from the file.

| Control | What it does |
|---|---|
| **Limit** | Stops after this many rows, up to 1,000,000. 5000 by default; a smaller number returns faster |
| **Filter** | Shows only the records containing the text **in any column**. It filters what is already loaded and does **not** read the file again |
| Quick filters | The same, column by column, with **Reset quick filters** to clear them all |
| **SQL Where** | Re-reads the file with a `WHERE` clause built on this file's columns. Unlike the filter boxes, **this narrows the read itself** |
| **Long names** | Shows SQL long column names instead of short system names, in the headings, in the filter form and in the `WHERE` clauses |
| **Export** | The records shown, with the filters applied, to CSV |
| **Add row** | Inserts a record. Physical files and tables only |
| **Refresh** | Reads again, **keeping the quick filters and the sorted column**, so you can watch one row change without setting the view up again |

**Editing a record.** Double-click a row and the editor shows every field. **Save**
writes the values back to the record on the server; **Cancel** closes without touching
it.

**The WHERE dialog** has a **Find column** box of its own, which matters on a file with
hundreds of columns, an **OK** that re-reads with the clause, and a **Clear** that
removes it and re-reads. A small **x** beside the filter line does the same from the
toolbar.

**The right-click menu** on a record row: **Navigate to Source** or **to Object**,
**Journal entries** for this file, **Object Change Impact** and **Open Source**.

A read that is taking too long can be stopped with **Cancel**, which keeps whatever has
come back.

---

## Dependents

The logical files, views and indexes built over this file, each with its object type,
description and SQL long name.

| Control | What it does |
|---|---|
| **Refresh** | Asks the database for the dependents again |
| **Filter** and quick filters | Narrow the list, with **Reset quick filters** |
| **Export** | The dependent objects shown, to CSV |

**The right-click menu**: **Open in File Viewer**, which walks from one dependent to
the next, **Open Source**, **Object Change Impact** and **Journal entries**.

This tab answers "who breaks if I change this record format" before the change,
instead of letting the compiler answer it afterwards.

---

## Columns/Fields

Every column with its type, length, decimals and text, including its position in the
record.

| Control | What it does |
|---|---|
| **Refresh** | Reads the definition again |
| **Filter** and quick filters | Show only the columns matching the text |
| **Export** | The column definitions, to CSV |

---

## RPG Data Structure

A data structure generated from the real file definition, ready to paste.

| Option | Choices |
|---|---|
| **Style** | **Full free**, **Free** (free-form declarations in columns 8 to 80, for use inside a fixed-format program), or **Fix** (a fixed-format D specification) |
| **Positions** | **Yes**, absolute positions, or **No**, fields packed contiguously |
| **Initialized from** | **Default**, each subfield from its data type's default, or **First record**, from the first record on the Data tab, falling back to the default for null or blank values |
| **Name** | A **prefix** and a **postfix**, `_ds` by default |
| **Add array** | Also declares an array of the structure and generates the code to populate it from the first records. Full free and free only |
| **Array size** | How many leading records to load, which is also the number of elements |

**Refresh** generates or regenerates it, **Copy** puts it on the clipboard, and
**Search** highlights text inside the generated source.

---

## Custom fields

Reading a file the way a legacy program reads a **program-described file**: you give
the layout, and the decoded values come back as a normal grid.

| Button | What it does |
|---|---|
| **Add field** | One row: name, position, type, decimals |
| **Input specs** | Imports the layout from fixed-format RPG input specs or a positional data structure, pasted into a window. **Import** reads it and fills the rows; **Cancel** closes without importing |
| **Open** / **Save** | Loads or keeps the layout as a local file. Saving changes nothing on the server |
| **Reset** | Clears every definition |
| **Refresh** | Reads the file and decodes the records with the layout |
| **Limit** | Stops after this many rows, up to 1,000,000 |
| **Export** | The decoded rows, to CSV |
| **SQL SELECT** | Writes the SQL that returns these same columns, typed, and opens it in a new editor |

**Each field row carries its own buttons:**

| Button | What it does |
|---|---|
| **‹** and **›** | Move this field one byte left or right. Hold **Shift** for ten |
| **«** and **»** | Move this field **and every row below it**, which is what you want when a field was inserted into the record |
| **↑** and **↓** | Move the row up or down. Hold **Shift** to send it to the top or the bottom |
| **✕** | Remove it. Hold **Shift** to remove it and every row below it |

The type list decides how those positions are read: as text, as a packed or zoned
number, as a date, and so on. A date kept in a numeric field reads as a date, and a
record that does not fit the layout says so in the cell instead of showing a number
assembled from bytes that are not one.

There is a guide for this one:
[A file described by its program]({{ site.baseurl }}/guides/program-described-file/).

---

## Small things that help

- The note explaining a tab opens from a question mark, instead of standing above the
  work.
- The line between the field definitions and the data can be dragged to give the room
  to whichever of the two you are working on, and a double click puts it back.

## Related

- [Journal Entries Viewer]({{ site.baseurl }}/tools/journal-entries-viewer/)
- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
