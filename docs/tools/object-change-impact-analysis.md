---
title: Object Change Impact Analysis
layout: default
parent: Object references
nav_order: 3
permalink: /tools/object-change-impact-analysis/
---

# Object Change Impact Analysis
{: .no_toc }

What a change to one object would break, and the order the rebuild has to run in.
{: .fs-5 .fw-300 }

For the whole job, read
[What a change would break]({{ site.baseurl }}/guides/change-impact/).
{: .fs-3 }

## Opening it

**Tools4i** in the Activity Bar, then **Object Change Impact Analysis**.

| Field | What it takes |
|---|---|
| **Object** | The name alone. Its type and library are found by searching the libraries below, and **the first match of each type is analyzed** |
| **Libraries** | Searched both for the object itself and for whatever references it. Spaces or commas, `*` allowed, in the order entered |
| **Recursive** | Also walks the call graph, to show who calls the programs that need recompiling |

**Analyze** finds everything the change would break. **Cancel** stops it, reporting
nothing.

## Results

Everything the change reaches, with **what has to happen to each one and why it is
affected**.

The "why" column is what makes the result reviewable. An object listed without a
reason is a list you have to trust; an object listed because a specific file is bound
into it is a list you can check.

Its **filter** narrows across object, library, type and the action needed, **Copy
list** puts the `LIBRARY/OBJECT` list on the clipboard, and **Export** writes the
rows shown to CSV.

## Recompile Order

The same objects arranged into a safe rebuild sequence: database objects first, then
service programs, then programs.

The order is the part people underestimate. Rebuilding the right objects in the wrong
order produces a second round of failures that look like new problems and are not.

Its **filter** narrows the steps by object, library or type, **Copy plan** puts the
ordered sequence on the clipboard, and **Export** writes it to CSV.

## Reading the recursive result

With **Recursive** on, the callers of the impacted programs are listed as well.

Read that as context rather than as a work list. A caller does not necessarily need
anything done to it; it is there so you know who feels the change.

## Acting from the list

The right-click menu offers:

- **View data (File Viewer)** on a file,
- **Open Source (read only)**,
- **Run action on N objects...**, which runs your own compile action over the
  selection,
- **Copy source of N objects to a library...**,
- **Save objects to a save file...**, which is the cheapest backup before a rebuild:
  the objects as they are now, in one file, before anything is recompiled over them.

The last three are what turn the analysis into the rebuild without retyping a list of
forty names.

## Taking it out

**Copy list** puts the `LIBRARY/OBJECT` list on the clipboard, **Copy plan** puts the
ordered rebuild sequence there, and both tabs export to CSV. **Save** keeps the whole
result as a snapshot.

## Related

- [Library Compile Order]({{ site.baseurl }}/tools/library-compile-order/)
- [Procedure Change Impact Analysis]({{ site.baseurl }}/tools/procedure-change-impact-analysis/)
