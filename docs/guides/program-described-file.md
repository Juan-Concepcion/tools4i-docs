---
title: A file described by its program
layout: default
parent: Guides
nav_order: 4
permalink: /guides/program-described-file/
---

# A file described by its program
{: .no_toc }

The file has one field. The record is 400 bytes of character data, and what those bytes
mean lives in an RPG program nobody has opened in years. Sometimes it is worse: the
record means one thing for one key and something else for another. This guide turns
that file into a grid you can read, filter and query.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Where it lives

Open the **File Viewer** on the file and go to the **Custom fields** tab. A layout
describes how to cut the record up: a name, a position, a type and the decimals, one
row per field.

You do not have to type it. A layout can be imported from the RPG input specifications
that already describe the file, or from a positional data structure, which is where
most modern programs keep the same knowledge.

## Getting the positions right

Positions are counted on the record as it really is, with each column taking the width
it actually occupies on disk rather than the width it appears to have. On a file whose
columns are not all character data, this is the difference between a layout that reads
and a layout that returns noise.

When a field lands a byte or two off, you do not retype the layout. Arrows on each row
move a field one byte at a time, carrying the rest of the layout along behind it, and
ten at a time with Shift. Shift on the row buttons reaches further: a field jumps to
the top or the bottom of the list, and Remove takes that field and every row under it,
naming what went.

The line between the field definitions and the data can be dragged, so you can give the
room to whichever of the two you are working on, and a double click puts it back.

## Dates that were never dates

A date kept in a numeric field is read as a date, packed or zoned, and a six-digit date
comes out with no extra digits in front of it.

If the field holds an eight-digit date with the century in it, the way RPG writes one,
mark it as such and it reads that way in the grid and in the SQL alike. A six-digit
field marked that way keeps reading as it did.

## When a record does not fit

A file that keeps a different record per key is full of records that do not match the
layout you are using, and that is the normal case, not a failure.

A record that does not fit says so in the cell. It does not show a number assembled
from bytes that are not a number, or a date that never happened, such as a month of 00.
The tab and the SQL it generates say it in the same place, so a result you export and a
result you read on screen agree.

This matters more than it sounds. A program reading that record would stop there, so a
viewer that renders it as a plausible value is hiding the thing you were looking for.

## Taking the layout to SQL

One button writes the SQL that returns those same columns, typed and ready to be
filtered, totaled or joined. It carries the filters you have on the grid, so it brings
back the rows you were looking at rather than the whole file.

That is the step that gets the data out of the viewer and into whatever else your shop
uses: a report, a join against a real table, a spreadsheet someone asked for.

## A working order

1. Open the file in the File Viewer and look at the **Data** tab first, to see what you
   are dealing with.
2. In **Custom fields**, import the RPG input specifications or the data structure if
   there is one. Type the layout only if there is not.
3. Read the first few rows. Fields that are one byte out show it immediately, and the
   arrows fix them without a retype.
4. Filter to one key value if the file keeps different records per key, and confirm the
   rows that do not fit are the ones you expect.
5. Generate the SQL and keep it. That is the piece that outlives the session.

## Related

- The **RPG Data Structure** tab of the File Viewer generates a data structure from a
  real file definition, in full free, free or fixed format, which is the opposite
  direction and often the next thing you need.
- **Dump Files Viewer** reads a record buffer out of a program dump as the file's own
  fields rather than as bytes, which is the same problem met from the other end.
