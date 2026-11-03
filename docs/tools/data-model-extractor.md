---
title: Data Model Extractor
layout: default
parent: Data model
nav_order: 1
permalink: /tools/data-model-extractor/
---

# Data Model Extractor
{: .no_toc }

Where a model starts: the objects and the declared relationships, read out of the
server or out of sources, into a staged model you can look at before you keep it.
{: .fs-5 .fw-300 }

For the whole job, from an undocumented library to a diagram, read
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

**Tools4i** in the Activity Bar, then **Data Model Extractor**.

The **model folder** at the top is where the model file is stored and loaded from.
**Browse...** changes it, and changing it here also changes the setting, so the whole
extension follows.

## The four sources

Each is a tab, and **Extract** reads from whichever one is in front.

| Tab | What it reads | Needs a connection |
|---|---|---|
| **Libraries and Objects** | The Db2 for i system catalog on the connected server | yes |
| **SQL script file** | A local `.sql` DDL script, a whole-schema export or individual tables, views and indexes | no |
| **Server Native Sources** | Native DDS and SQL DDL source members read from the server | yes |
| **Local Native Sources** | The same, from a folder holding source subfolders | no |

### Libraries and Objects

Choose the scope: **libraries**, up to five, separated by commas or spaces, or a
single **item**, by name or by a wildcard such as `ABC*`, searched in each of those
libraries.

### The two native-source tabs

Both ask which source files or subfolders to read, defaulting to
`QDDSSRC, QSQLDDLSRC`, and both decide the parser by the name: a name containing
**DDS** is read as DDS physical and logical files, anything else as SQL DDL.

**Members** narrows to the ones whose name matches a pattern, and **default schema**
decides the schema given to objects whose name is not schema-qualified in the source,
which is every DDS file. Names that carry their own schema keep it.

## The result, before it is kept

Extraction writes to a **staged** copy. The real model file is untouched until you
save, and four tabs show what the pass produced:

| Tab | What it lists |
|---|---|
| **Items** | The tables, files, views and indexes |
| **Dependencies** | Every relationship: foreign keys, implied ones, logical over physical, view over table, index over table, and the ones added by hand |
| **Implied FK** | Candidates and confirmed implied foreign keys |
| **Items excluded** | Items you took out, which stay out and are **skipped by every later extraction** until you include them again |

Excluding and deleting are not the same thing, and the difference matters. An excluded
item stays excluded; a deleted item simply leaves, and the next extraction brings it
back.

## The implied foreign keys

**Find candidates** analyzes the model **locally**: it matches each table's primary or
unique key columns, by name and type, against the other tables, and proposes what
looks like a relationship.

**Confirm with Server** validates each candidate against the data, counting the rows
that would be left orphaned. A candidate with no orphans becomes a confirmed implied
foreign key. One that leaves thousands is telling you two fields share a name and
nothing else.

## Saving, or not

The **unsaved mark** appears while anything is staged. It opens the list of everything
waiting, and from there:

- **Save changes** makes them permanent in the model file,
- **Discard** throws the staging away and goes back to the saved model.

## Speed

Building from a large library reads many source members in one trip rather than one
trip each, and asking what a library holds takes one question instead of five.

## Related

- [Data Model Editor]({{ site.baseurl }}/tools/data-model-editor/)
- [Data Model Comparison]({{ site.baseurl }}/tools/data-model-comparison/)
