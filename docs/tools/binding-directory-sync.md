---
title: Binding Directory Sync
layout: default
parent: Binding directories
nav_order: 2
permalink: /tools/binding-directory-sync/
---

# Binding Directory Sync
{: .no_toc }

Two binding directories side by side, a target and a base, with a verdict per entry
and one action that brings the target in line.
{: .fs-5 .fw-300 }

## What it is for

The case where a development binding directory has drifted from the one production was
built with, and nobody knows by how much.

## Opening it

**Tools4i** in the Activity Bar, then **Binding Directory Sync**.

| Field | What it takes |
|---|---|
| **Target** library and name | The one that will be reconciled to match the base |
| **Base** library | The reference. **Leave it empty** to take the first match in the library list, skipping the target library |
| **Base** name | Leave it empty to compare against one with the same name as the target |

Leaving both base boxes empty is the common case: the same name, found the way the
binder would find it.

A **quick filters** switch adds a box over each column of the result.

## The six verdicts

| Verdict | What it means |
|---|---|
| **In sync** | Same entry, same qualification |
| **Re-qualified** | The same object, but named with a different library |
| **Out of sync** | Present in both, bound with a different type or activation |
| **Added in Target** | An extra the base does not have |
| **Added in Target, different qualifier** | An extra, and qualified differently |
| **Missing in Target** | The base has it, the target does not |

**Out of sync** is the one that produces the failure nobody can explain, because both
sides look like they have the entry.

## Acting on one entry

| Entry | What it does |
|---|---|
| **Copy from Base** | Brings the base entry across as it is |
| **Copy from Base and Re-qualify to Target** | Brings it across, pointing at the target's own library |
| **Re-qualify from Base** / **Re-qualify to Target** | Changes which library an existing entry points at |
| **Remove from Target** | Takes the extra out |

The re-qualify entries are what you want when development and production hold the same
objects in differently named libraries, which is most shops.

## Or all at once

**Reconcile Target with Base** adds what is missing, removes what is extra, and aligns
the type and activation differences, in one action.

Read the lists before running it. "Added in Target" is not always wrong; sometimes the
target is ahead on purpose, and that is exactly the case where you want the per-entry
actions instead.

Only the **target** is changed. The base is read.

## Related

- [Binding Directory Editor]({{ site.baseurl }}/tools/binding-directory-editor/)
