---
title: SavF Manager
layout: default
parent: Transfer
nav_order: 2
permalink: /tools/savf-manager/
---

# SavF Manager
{: .no_toc }

Save files as a list you can read: what each one holds, what is inside it, and what
can come out of it.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **SavF Manager**.

The **library** box takes a library name or a special value: `*ALLUSR`, `*LIBL`,
`*CURLIB` or `*ALL`. **Refresh** lists them again, picking up anything created or
deleted since.

## The columns

Library, name, description, **objects**, **saved libraries**, compression, **size**,
**updated** and **owner**.

Size and updated together answer most of the questions a full disk raises, and
"objects" says whether the save file is empty without opening it.

**Compression** is one of `*NO`, `*LOW`, `*MEDIUM`, `*HIGH`, `*YES` or `*DEV`, which is
worth reading before a restore: a heavily compressed save file costs processor time to
read back, and that is the difference between a ten-minute restore and an hour.

## The right-click menu

| Entry | What it does |
|---|---|
| **Show info** | The save file's own attributes |
| **Display saved objects** | What is inside it, as a list |
| **Save here** | **Objects...**, **Library...**, or **More objects (append)...** into this save file |
| **Restore** | **All...**, or from the object list, **Restore this object to...** a library you choose |
| **Download...** | The save file to this machine |
| **Copy to library...** | |
| **Clear...**, **Delete...** | Both ask first |
| **Copy Name** | Name, or **Name and location** |
| **Reveal in Navigate** | Opens it in the browser |
| **Filter to this library**, **Filter to this type** | Narrows the list to what you clicked, without retyping a filter |

Inside the object list, **Show object detail** opens everything the save file records
about one saved object, which is how you check a restore will bring what you expect.

**Restore this object to...** is the common case and the awkward one everywhere else:
you want that one program back, into a test library, not over the top of production.

## Creating and moving

- **New SavF...** creates one.
- **Upload SavF...** sends a local `.savf` to the server.
- **Download...** brings one back.

So a save file sent by a vendor, or one going to support, does not need a separate
transfer tool.

## While it works

A long operation can be stopped with **Cancel**, which stops waiting for the server
and discards the operation.

## Related

- [Navigate Server]({{ site.baseurl }}/tools/navigate-server/), whose library menu can
  save a whole library straight into a save file.
