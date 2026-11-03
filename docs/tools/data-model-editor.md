---
title: Data Model Editor
layout: default
parent: Data model
nav_order: 2
permalink: /tools/data-model-editor/
---

# Data Model Editor
{: .no_toc }

Everything an extraction cannot know: the links that live only in the code, the
columns that feed each other, and the names the business uses.
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

**Tools4i** in the Activity Bar, then **Data Model Editor**.

## The seven tabs

| Tab | What it holds |
|---|---|
| **Items** | Every table, view, index and logical file in the model, the things a diagram is drawn from |
| **Dependencies** | How the items are linked: foreign keys, index and view dependencies, logical over physical |
| **Implied FK** | Candidates and confirmed implied foreign keys |
| **Processes** | The business processes you define, and the items each one touches: the model in the terms your work uses |
| **Diagrams** | Saved diagrams, a chosen set of items laid out and kept, to reopen in the Viewer |
| **Items excluded** | Items taken out of the model, skipped by every extraction until you include them again |
| **Health** | Missing, duplicate and orphan items, and dangling relationships |

### What the tables show

**Items** carries the schema, the name (short and long), the type, its **keys**, how
many **relationships** touch it, its **note**, the **source** it came from, and the
**result** of the last action on it.

**Dependencies** carries the child item, what it **depends on**, the parent item, and
the same source and result.

**Implied FK** is the widest: child and parent as **references** and **referenced**,
the **column pairs**, the **confidence**, and after a server confirmation the
**number of records**, the **orphan records** and the **percentage that match**, which
is the number the confidence thresholds are read against.

An item can carry a **note** of its own, and a diagram can pin that note beside the
item on the canvas.

Above the tables, a **source filter** shows items from every source or narrows to one,
and the type and kind chips count what is in front of you and filter to it in a click.
Two tick boxes narrow the Items and Dependencies tabs to the **duplicates** only.

## Adding and editing

**New item** opens the form for a data item. A dependency already recorded is not
added a second time, and it says so rather than quietly duplicating.

On a link, the editor carries the part no extraction can produce:

**Which column feeds which.** A link can hold its column pairs, so the model records
where a value comes from and not merely that two items are related. The columns
offered are the ones whose value **fits** where it is going, by type and by size, and
a tick beside each pair opens the list to every column, for when you know better. The
candidate list opens on the field, narrows as you type, walks with the arrow keys, and
shows each column's type beside its name.

**What the link turns out to be.** Between two tables, a link counts as a **foreign
key** while its columns are the same type on both sides, and as a **dependency** when
they are not. It is settled whenever the columns change, and said at the time, naming
the two columns that decided it.

**Check on server** reads the whole relationship from the catalog: every column it
names, the type on each side, and the link itself, whether that is a constraint, a
view over a table, a logical over its physical or an index over its table. It only
looks, writes nothing anywhere, and reports what does not match instead of changing
it.

## The right-click menu on an item

The order is deliberate: the entries that change nothing come first, then the ones
that edit the model, then the two that take the item out of it.

| Entry | What it does |
|---|---|
| **Edit** | Opens the item form |
| **Copy name** | **System name**, **Long name**, or **Qualified**, as schema and name. On a selection, **Copy names** |
| **Reassign schema...** | Moves the item to another schema, which is the routine fix after extracting with the wrong default |
| **Delete** | Takes it out. The next extraction brings it back |
| **Exclude** | Takes it out **and keeps it out**, skipped by every later extraction |

Delete and Exclude sit at the end, away from the routine entries, because they are the
two that are hard to undo by accident.

On a relationship row the menu offers **Relationship Info**, which opens the link in
full: its kind, its column pairs with the type on each side, and which end is the
child and which the parent.

## Implied foreign keys

**Find candidates** matches each table's primary or unique key columns, by name and
type, against the other tables, locally. **Confirm with Server** validates each
candidate against the data, counting the orphan rows. No candidate enters the model on
a guess.

## Processes

**New** defines a business process, and items are assigned to it from here or from the
diagram. A saved **diagram** row offers **Open in Viewer**, **Rename...** and
**Delete**, so the diagrams kept in the model are managed from the same place. A
process is what makes a readable diagram possible later: you add the process, not
thirty files.

## Health

What a model accumulates as the application changes under it: relationships pointing
at items that are not there, **missing referenced items** that a relationship names
but the model does not hold, duplicated items and duplicated relationships, items
nothing connects to, and redundant access paths. Each finding jumps to the item it is
about.

Two of them read as advice rather than as errors. **Covered by** says another access
path already covers this one, and **check before removing** marks the ones where that
is true but worth a look first: an index nothing seems to use may still be the one a
query plan picked.

## Sharing the model

| Button | What it does |
|---|---|
| **Push to Server** | Publishes your local model to the server folder, **replacing the shared copy** for everyone who pulls it |
| **Pull from Server** | Fetches the shared model and **replaces your local copy**. Anything unsaved here is lost |

Both are blunt on purpose: this is a file, not a merge tool. Save before pulling.

## Saving, or not

The **unsaved mark** appears while anything is staged, and opens the list of what is
waiting, with **Save changes** and **Discard** beside it. The real model file is
untouched until you save.

## Related

- [Data Model Viewer]({{ site.baseurl }}/tools/data-model-viewer/)
- [Data Model Dictionary]({{ site.baseurl }}/tools/data-model-dictionary/)
- [Data Model Comparison]({{ site.baseurl }}/tools/data-model-comparison/)
