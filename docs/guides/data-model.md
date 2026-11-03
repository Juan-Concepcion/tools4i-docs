---
title: Modeling an inherited database
layout: default
parent: Guides
nav_order: 1
permalink: /guides/data-model/
---

# Modeling an inherited database
{: .no_toc }

You have an application nobody documented, a library full of files, and a question that
starts with "if I change this, what else". This guide goes from the objects and the
sources already on the server to a diagram you can put in front of someone, and to a
model that keeps what you learned on the way.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## What you end up with

A **model**: one file, kept where you choose, holding the items (files, tables, views,
indexes, logicals), how they are linked, what the columns mean, which of them hold
personal data, the business processes you grouped them into, and the diagrams you drew.
It is yours, it is a file, and it can be published to the IFS for the rest of the team.

What it is not is a copy of the catalog. A model holds the part a catalog cannot: the
links nobody declared, and the meaning nobody wrote down.

## The one rule to know before you start

Every tool here works on the **same staged copy** of the model. Extracting, editing,
drawing and comparing all write to that copy, and nothing reaches the model file until
you press **Save changes**. **Discard** puts everything back to the last save.

While changes are waiting, the toolbar carries a mark. That mark opens the list of what
is waiting, with Save and Discard beside it, so you can always answer "what am I about
to write" before you write it.

## Step 1. Take the skeleton from the server

Open the **Data Model Extractor** and choose where the first pass reads from. There are
four sources, and they do not know the same things.

| Source | What it knows | What it misses |
|---|---|---|
| The Db2 catalog | What exists right now: files, tables, views, indexes, logicals over their physicals, and the constraints that were actually declared | Anything that was never declared to the database |
| Native DDS and SQL sources on the server | The definitions as they were written, a view's columns among them | Objects whose source is not there any more |
| Sources on this machine | The same, for a project you already downloaded | The same |
| A DDL script | Whatever the script creates | Everything outside the script |

Take a whole library or a single object, and choose whether the pass **merges** into
what you have or **replaces** it. The result is staged, so a bad pass costs you a
Discard and nothing else.

Start with the catalog, over the library the application runs in. It is the fastest way
to get every object and every declared relationship in one go, and it is the only
source that reflects what is on the system today rather than what someone once intended.

## Step 2. Accept what an extraction cannot find

This is the step that decides how useful the model becomes.

In an application written before constraints were common, almost nothing is declared.
Two files are joined by a program reading one and chaining to the other, by a field
holding the same value in two places, by a convention everybody knew in 1997. The
catalog has no record of any of it, so no extraction can produce it.

After the first pass you have the objects, the keys, the access paths and the handful
of declared constraints. The relationships that matter to the business are still
missing. The next three steps are how they get in.

## Step 3. Let the analysis propose the undeclared keys

**Implied foreign keys** looks for the shape of a relationship that was never declared:
a table holding every column of another table's key. Each candidate comes rated by
confidence.

Nothing enters the model on a guess. Each candidate is confirmed against the catalog or
against the data itself, counting the rows that would be left orphaned if the
relationship were real. A candidate that leaves thousands of orphans is telling you
something, and usually it is that two fields share a name and nothing else.

Confirm the ones that hold. They enter the model marked as worked out rather than
extracted, and the diagram keeps that distinction visible later.

## Step 4. Record what only a person knows

Open the **Data Model Editor** for everything the machine cannot reach.

**Add the links that exist only in the code.** A dependency says this item needs that
one. Add it from the item's own form, or draw it straight on the diagram.

**Say which column feeds which.** A link can carry its column pairs, so the model holds
where a value comes from and not merely that two items are related. Name them as you
create the link, fill them in later, or leave them until you know. The columns offered
are the ones whose value fits where it is going, by type and by size, and a tick beside
each pair opens the list to every column, for when you know better than the model does.

**Let the link decide what it is.** Between two tables, a link counts as a **foreign
key** while its columns are the same type on both sides, and as a **dependency** when
they are not. It is settled whenever the columns change, and it is said at the time,
naming the two columns that decided it. You do not have to remember the rule. You have
to read the sentence it gives you.

**Check it against the server.** Any relationship can be checked against the catalog:
every column it names, the type on each side, and the link itself, whether that is a
constraint, a view over a table, a logical over its physical or an index over its
table. The check only reads. It writes nothing, anywhere, and it reports what does not
match instead of changing it.

## Step 5. Draw only the part you are explaining

Open the **Data Model Viewer**. A diagram here is not a picture of the library. It is a
picture of an explanation.

Add one item, add its related items, or add a whole business process, and the diagram
grows around the thing you are describing. Nobody can read four hundred files on one
canvas, and nobody needs to.

IBM i objects are drawn as what they are: physical files, logical files and
multi-format logical files sit over the physicals they are built on, alongside tables,
views and indexes.

### Reading a line

Every line says three things at once, so a diagram can be read without a key beside it.

- **The dash says where the link came from.** Solid, it was extracted from the server.
  Dashed, a person added it. Dotted, the analysis worked it out and someone confirmed
  it.
- **The head says what the link is.** A foreign key is drawn on the heaviest line. A
  plain dependency carries nothing. A dependency that carries column pairs says so, and
  says whether those pairs fit the column they feed.
- **The color says which of the two items is the one that depends.**

Click a line and you get the whole of it: how it was recorded, how it is drawn, its
column pairs with the type on each side, and whether each pair fits.

### Drawing a link on the canvas

Hold **Ctrl and Alt**, click the item that depends, then click the one it depends on.
An arrow follows the cursor while you choose, and when you land, the link opens ready
for its columns.

### Taking it out of the tool

A diagram saves, reopens and exports, as an image or as a document. The export carries
the legend, and the exported document draws every link the way the canvas drew it, so
somebody who never opened the tool reads the same three things from a line.

## Step 6. Say what the columns mean

The **Data Model Dictionary** is a business glossary at column level, with one row per
**distinct column definition**. That distinction is the whole point: two columns sharing
a name but not a data type are two different things, and describing them as one produces
a glossary that is wrong in a way nobody notices.

Each row carries its business description, the text the source already had, a "used by"
cross-reference across the model, and a measure of how much of the model is documented.
It exports to CSV or Markdown, which is usually how it reaches the people who asked for
documentation in the first place.

**Personal data classification** lives here too. Detection proposes candidates from the
column name, the source text and the description, and applies nothing on its own: every
proposal goes through a review dialog. It warns when the same column name is classified
in some files and not in others, because under-tagging is the real exposure, and when a
classification has come loose because the column definition changed, so it can be
reattached or dropped deliberately rather than silently.

## Step 7. Keep it honest

A model accumulates damage as the application changes under it. **Model health checks**
name that damage: relationships pointing at items that are not there, references to
items missing from the model, duplicated items and duplicated relationships, items
nothing connects to, and redundant access paths. Each finding jumps to the item it is
about.

**Data Model Comparison** answers the other question: what changed since. Compare your
model against the server as it is now, against another model file, or one library
against another. Every difference is stated as work to do in **your** model, add,
remove or update, across the objects, the links, the processes and the saved diagrams.
Objects, dependencies, processes and diagrams can be brought across from the panel
itself.

The **Impact** column is the one to read before accepting anything. It says what a
change reaches beyond the model: a program that may need recompiling, glossary entries
that would come loose, the diagrams and processes the object appears in.

## A first afternoon

1. Extract the application library from the Db2 catalog. Look at what came in, and save.
2. Run the implied foreign keys. Confirm the ones that survive their check, discard the
   rest, and save.
3. Pick the one question people keep asking you, such as how an order reaches a general
   ledger entry. Put those items on a diagram and nothing else.
4. Every time the diagram cannot answer the question, you have found a link nobody
   declared. Draw it, name its columns, and read the sentence the tool gives you about
   what it turned out to be.
5. Write the business description of the ten columns that appear in every argument.
6. Export the diagram and the glossary, and send them to whoever has been answering
   these questions from memory.

By the end of it the model holds something the catalog never did, and the next person
who inherits the application starts at step 3.

## What this does not do

- It does not change the server. Checking a relationship against the catalog only reads.
- It does not need anything installed on the system.
- It does not claim a relationship the data does not support. A proposal is confirmed
  against the catalog or against the data before it can enter the model.
