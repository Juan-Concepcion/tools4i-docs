---
title: Library Compile Order
layout: default
parent: Object references
nav_order: 4
permalink: /tools/library-compile-order/
---

# Library Compile Order
{: .no_toc }

Every source member of a library in an order where nothing is built before what it
depends on.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Library Compile Order**.

| Field | What it takes |
|---|---|
| **Source library** | The library whose members are to be built. Everything in the order comes from here |
| **Source files** | Which source **files** in that library to read, such as `QRPGLESRC`. Not libraries and not members. Wildcards allowed; empty means every `Q*` source file |
| **Libraries** | The libraries searched to work out what each member builds and what it depends on, in the order entered |

The second and third boxes are the ones people confuse. The first says where the
sources are; the third says where to look for the objects they reference.

**Analyze** reads the members and orders them. **Cancel** stops it, reporting nothing.

## The order

Files first, then modules, then service programs, then programs. Within each step the
members are ordered by what depends on what.

If your change crosses libraries, build the list for each one and keep the same order
between them.

## Acting from the list

The right-click menu carries the rebuild itself:

| Entry | |
|---|---|
| **Run action on N members...** | Runs your own compile action over the selection, in the order shown |
| **Copy source of N members to a library...** | |
| **Open Source (read only)** | |
| **View data (File Viewer)** | On a member that builds a file |
| **Copy Member Name**, **Copy Object Name** | |

## Taking it out

**Copy list** puts the ordered `LIBRARY/OBJECT` list on the clipboard, **Export**
writes CSV, and **Save** keeps the order as a snapshot for the next rebuild.

## Related

- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
- [Object and Sources]({{ site.baseurl }}/tools/object-and-sources/)
