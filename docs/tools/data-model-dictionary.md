---
title: Data Model Dictionary
layout: default
parent: Data model
nav_order: 4
permalink: /tools/data-model-dictionary/
---

# Data Model Dictionary
{: .no_toc }

A business glossary at column level, with one row per distinct column definition, and
the sensitive-data classification that goes with it.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Data Model Dictionary**.

**Refresh** re-reads the model file from disk, which is what you press after
extracting or editing the model in another panel.

## The columns of the table

| Column | |
|---|---|
| **System name** | The short name |
| **Long name** | The SQL name |
| **Datatype**, **Length**, **Precision** | The definition that makes this row distinct |
| **Used by** | A cross-reference: which items carry this column |
| **Sensitivity** | **NPI**, **PII**, or **not classified** |
| **Protection** | **Encrypted**, **not protected**, or **not reviewed**, which is the state a column starts in |
| **Description** | The business meaning, which is the part you write |

One row per **distinct definition**, not per name. Two columns sharing a name but not
a data type are two different things, and describing them as one produces a glossary
that is wrong in a way nobody notices.

## Narrowing it

| Control | What it does |
|---|---|
| **Search** | Filters across system name, long name, datatype, source text and description |
| **Undocumented only** | Shows only the columns with no glossary description yet. **Source text from the extraction does not count as documented** |
| **Inconsistent only** | Shows only the column names that appear with more than one datatype, length or precision across items |
| **Sensitivity** | Filters by classification |

**Inconsistent only** is the shortest route to the real problems in an old database:
the same field name holding different things in different files.

## Actions

Three ways to fill the dictionary in from what the model already knows, rather than by
typing:

| Action | What it proposes |
|---|---|
| **Register encryption found in the source text** | Columns whose source text says they are encrypted, so the Protection column reflects it |
| **Classify sensitive data** | Classifications from a **pattern scan** over the column names and a **source text scan**, proposing **NPI**, **PII** or neither |
| **Suggest descriptions** | Business descriptions seeded from the text the sources already carry |

Every one of them **proposes**; nothing is applied on its own. The review dialog shows
the proposals with **Select all** and **Select none**, and **Apply selected** saves
only the ticked ones. **Discard ticked** permanently deletes entries, and is meant for
the case where the column is genuinely gone.

## Classifications that came loose

**Review...** appears when a column's datatype or long name changed, or its item was
removed, so the entries attached to it stopped applying.

From there each one can be **reattached** to the column's new definition or dropped.
That is the difference between a glossary that ages and one that quietly stops being
true.

## Exporting

**Export** offers four documents:

- two spreadsheets: one row per column, or **one row per column and item pair**, one
  line per usage, which is the one to use when somebody asks which files a sensitive
  column appears in,
- two written reports: the dictionary reference, and the sensitive-data report.

That is usually how this reaches the people who asked for documentation.

## Saving

The **unsaved mark** appears while anything is waiting, here or in another Data Model
panel, with **Save changes** and **Discard** beside it. The saved file is untouched
until you save.

## Related

- [Data Model Editor]({{ site.baseurl }}/tools/data-model-editor/)
- [Data Model Comparison]({{ site.baseurl }}/tools/data-model-comparison/)
