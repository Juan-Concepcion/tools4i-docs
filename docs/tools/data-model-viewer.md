---
title: Data Model Viewer
layout: default
parent: Data model
nav_order: 3
permalink: /tools/data-model-viewer/
---

# Data Model Viewer
{: .no_toc }

Where the entity-relationship diagrams are built, including the objects that only exist
on IBM i.
{: .fs-5 .fw-300 }

For the whole job, read
[Modeling an inherited database]({{ site.baseurl }}/guides/data-model/).
{: .fs-3 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Data Model Viewer**. The canvas opens empty:
a diagram is something you build, not the library drawn for you.

## The toolbar

| Button | What it does |
|---|---|
| **Load diagram** | Opens a saved diagram: **from a local file**, or **from the data model**, where diagrams are kept inside the model file itself |
| **Save diagram** | Saves the arrangement, the notes and the filters, **to a local file** or **to the data model** |
| **Export PNG** | Opens the export dialog described [below](#the-export-dialog) |
| **Export documentation** | Writes a Markdown file with a diagram of the canvas plus each item's details |
| **Add to Diagram** | Adds a single item, every item matching a name, or a whole process |
| **Undo** / **Redo** | Ctrl+Z and Ctrl+Y, over the canvas changes |
| **Unsaved changes** | Appears only while the model has changes waiting. Opens the list of what they are, with Save and Discard |
| **Multi-select** | Switches between selecting one item and selecting several |
| **Find** | Jumps to an item already on the canvas |
| **Pan** left, up, down, right, and **Center** | Moves the view without the mouse |
| **Zoom out**, **Zoom in**, **Fit to view** | The usual three |
| **Zoom to area** | Click it, then drag a box on the canvas to zoom to exactly that. Esc cancels |
| **Re-layout** | Rearranges every item on the canvas with the current layout |
| **Clear** | Removes every item from the canvas. The model is untouched |

## The item type filters

**Item Types** opens them: six checkboxes, all on at first. They do not remove
anything from the model; they decide what the canvas draws.

| Filter | What it covers |
|---|---|
| **Table** | Physical files and SQL tables |
| **Logical** | Logical files, including multi-format and join logicals |
| **View** | SQL views and materialized query tables |
| **Index** | SQL indexes |
| **Query** | Query definitions and what they read |
| **Other** | Aliases and anything else |

Turning **Index** off is the usual first move on a library with hundreds of them, when
what you are explaining is the data and not the access paths.

## The display toggles

| Toggle | What it shows |
|---|---|
| **Notes** | The notes pinned to the canvas |
| **Long names** | SQL long names instead of short system names |
| **Legend** | A small key of colors, shapes and relationship lines, over the chart |
| **Element Info** | The details panel on the right |
| **Minimap** | A small overview of the whole canvas, with a rectangle marking the visible area. Drag the rectangle to move the view |

Both the legend and the minimap have a close button of their own, so they can also be
dismissed from the panel rather than from the toolbar.

The summary of the model, where the panel says which file it is working on, carries a
**Reveal file** button that shows that file in the operating system's file explorer.
Useful when two people are not sure they are looking at the same model.

## Working on the canvas

**Selecting.** With multi-select off, a click selects one item. With it on, Ctrl+click
adds to the selection and dragging a box selects everything inside it.

**Drawing a link.** Hold **Ctrl and Alt**, click the item that depends, then the one it
depends on. An arrow follows the cursor while you choose, and the link opens ready for
its columns. Releasing either key cancels.

**Reading a line.** Three channels at once:

- **The dash** says where the link came from: solid, extracted from the server; dashed,
  added by hand; dotted, worked out by the analysis and confirmed.
- **The head** says what it is: a foreign key on the heaviest line, a plain dependency,
  a dependency that carries column pairs, and one whose pairs do not fit the column
  they feed.
- **The color** says which of the two items is the one that depends.

Click a line and the inspector gives you the whole of it: how it was recorded, how it
is drawn, its column pairs with the type on each side, and whether each pair fits.

On a declared foreign key it also shows what the constraint itself says: its name, the
items it **references**, its **on delete** and **on update** rules, and its **check
clause** when it has one. Those four are the difference between "these two are
related" and "the database will refuse the delete".

## Adding items from a list

**Add to Diagram** opens a list of what the model holds. An item already on the canvas
is marked as such; every other row carries an **Add** button, so a diagram can be
built row by row without closing the dialog.

The same dialog adds a whole **process**, which is the fast way to draw a subject
rather than a set of files, and the relationship rows show each link's **kind** beside
the items it joins.

## Right-click on an item

The menu changes with how many items are selected. With **one** item:

| Option | What it does |
|---|---|
| **Add related items** | A submenu: **Dependents on X**, **Items X depends on**, or **All** |
| **Remove from canvas** | Takes it off the diagram. The model is untouched |
| **Re-layout related** | Rearranges that item and its neighbors, with a submenu of the layouts |
| **Add to process...** | Puts it in a business process |
| **Show Item Note** | Only when the item has a note that is not already pinned on this diagram |
| **Copy name** | A submenu: **Name**, or **Name and location** |
| **File viewer** | Opens the object's data |
| **Navigate** | A submenu: **to Object**, or **to Source** |

With **several** items selected, the same menu counts them: *Add related items (4)*,
*Remove 4 items*, *Add 4 items to process...*, *Copy names*.

The last three entries, **Show Item Note**, **File viewer** and **Navigate**, apply to
a single extracted object, so they are not offered on a multiple selection, nor on an
item that is on the canvas but not in the model.

## Right-click on the background

The canvas itself has a menu, so the whole toolbar is reachable without crossing the
screen. It carries the same state as the toolbar: a toggle shows a tick when it is on,
and the current layout is marked.

| Group | Entries |
|---|---|
| **Load diagram** | From local file..., From the data model |
| **Save diagram** | To local file..., To the data model |
| **Export** | PNG..., Documentation... |
| **Add to Diagram...** | The same dialog as the toolbar button |
| **View Items** | The six type filters, each with its tick |
| Display | **Long names**, **Legend**, **Element Info**, **Minimap**, **Notes** |
| Finding | **Find...**, **Multi-select** |
| View | **Fit to view**, **Zoom to area**, **Center**, **Re-layout** (with the layouts, the current one marked) |
| **Add note here** | Pins a note at the point you right-clicked |

**Add note here** is the one that only exists in this menu. It uses the position of the
click, which is why it cannot sit on the toolbar.

A menu opened near the bottom or the right of the window stays on screen, and its
submenus flip to the left when there is no room on the right.

## The export dialog

**Export PNG** asks four things before writing anything:

| Option | Choices |
|---|---|
| **Scope** | **Full**, every item however far outside the visible area it sits, or **View**, only what is on screen now, at the current zoom |
| **Scale** | **1x** screen size, **2x** sharp enough for a slide or a document (the default), **3x** for printing or a very large diagram |
| **Legend** | Draw the key into the image. It is placed where it covers no item and no line |
| **Notes** | Draw the pinned notes into the image as well |

**Export documentation** writes Markdown instead: a diagram of the canvas plus each
item's details, with every link drawn the way the canvas draws it, legend included.

## Find

**Find** takes the name of an item already on the canvas. The start of a name is
enough, and the long name works too. It scrolls the canvas to the item and selects it.

Its own result list also offers **Find on canvas** above the usual item menu, so you
can act on what you found without closing the dialog first.

## Related

- [Data Model Editor]({{ site.baseurl }}/tools/data-model-editor/)
- [Data Model Comparison]({{ site.baseurl }}/tools/data-model-comparison/)
