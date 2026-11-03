---
title: Data Model Comparison
layout: default
parent: Data model
nav_order: 5
permalink: /tools/data-model-comparison/
---

# Data Model Comparison
{: .no_toc }

What changed since: your model against the server as it is now, against another model
file, or one library against another.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Data Model Comparison**.

## The three comparisons

| Mode | What it compares |
|---|---|
| **Live** | Your saved model against the server as it is now |
| **File** | Your saved model against another model file, chosen with **Choose file...** |
| **Library** | One library against another: **A** is the library being brought up to date, every row is a change to make in **A**, and **B** is the one A should end up matching |

**Compare** runs it. Comparing only reads: your model changes only when you apply a
row from the table.

## The options, and what they cost

| Option | What it does |
|---|---|
| **Thorough (much slower)** | Adds SQL foreign keys and file dependencies: logical over physical, view over table |
| **Include queries (slower)** | Brings query definitions into the comparison |
| **Re-read the server** | Ignores what was read before and asks again |

Narrowing the comparison skips the catalog queries for what you leave out, which is
why the two slow options are off by default rather than hidden.

## The four tabs

| Tab | What it reports |
|---|---|
| **Items** | Objects present on one side only, and what differs inside the ones on both: columns, keys, record formats |
| **Dependencies** | How the objects are linked: foreign keys, implied relationships and file dependencies |
| **Processes** | Added, removed, renamed, or covering a different set of objects |
| **Diagrams** | Added, removed, or changed in the objects they show, their layout or their notes |

Every difference is stated as **work to do in your model**: add, remove, update. Not
as a neutral list of discrepancies you then have to interpret.

Each row carries **To do**, **Before** and **After**, so what the change actually is
can be read without opening anything. Double-click a row to see the object or
dependency in full, with every difference marked on it.

## Only what can break a program

**Recompile only** shows just the changes that can level-check a compiled program:
a column added, removed or retyped, a key change, a record-format change.

That turns a comparison of four hundred differences into the ten that will stop
something at run time, which is usually the list somebody is waiting for.

## Bringing changes across

Objects, dependencies, processes and diagrams can be applied from the panel itself.
The change is held unsaved until you save it, and **Discard** puts applied rows back
to being differences.

A process or a diagram that both models have offers a choice: **replace** it with the
other version, or **merge** what the other has into yours, keeping everything already
there.

## The Impact column

Read this before accepting anything. It says what a change reaches beyond the model: a
program that may need recompiling, glossary entries that would come loose, and the
diagrams and processes the object appears in.

A column added to a file is a small difference in the model and a large one in the
building.

## Exporting

**Export** writes the rows currently shown, the tab you are on with its filters, as
CSV. **Export MD** writes the same as a Markdown report, which is the one to attach to
a change request.

## Related

- [Data Model Extractor]({{ site.baseurl }}/tools/data-model-extractor/)
- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
