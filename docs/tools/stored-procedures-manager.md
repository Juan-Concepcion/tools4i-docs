---
title: Stored Procedures Manager
layout: default
parent: Database
nav_order: 1
permalink: /tools/stored-procedures-manager/
---

# Stored Procedures Manager
{: .no_toc }

SQL procedures and functions found by what you remember about them, including the text
inside the definition itself.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Stored Procedures Manager**.

## Finding one

| Filter | What it takes |
|---|---|
| **Schema** | The library to look in. Empty means every schema. Wildcards allowed |
| **Type** | Procedures, which are called with `CALL`, or functions, which return a value and are used inside a query |
| **Name** | Routines whose name contains the text |
| **External program** | `LIBRARY/PROGRAM` contains the text, which is how you find the routine behind a program you already know |
| **Definition contains** | Text to find **inside the routine's SQL**. This is the slow part of the search: leave it empty when you can |

Searching the body is what makes this better than a catalog query, because it finds
the routine that writes to the table you are about to change. It just costs more, and
the panel says so.

Listing stays quick even when a routine's program lives in a system library: the read
asks for the programs the routines name rather than for everything that library holds.

## The right-click menu

| Entry | What it does |
|---|---|
| **View definition** | The SQL the routine was created with |
| **Copy definition (DDL)** | The same, on the clipboard |
| **View parameters** | The parameter list, with types and direction |
| **Generate CALL template** | A `CALL` with the parameters in place, ready to fill in. **Copy** puts it on the clipboard |
| **Run...** | Calls the routine on the server with the values you give. It runs for real: anything it changes, it changes |
| **Drop...** | One row. On a selection it becomes **Drop selected (N)...** |
| **Copy Name** | **Name**, **Name and Location**, **Specific Name** or **External Program** |

The template is the part that saves the time: getting the parameter order and types
right by hand is where the typos live.

The **specific name** is the one to copy when a schema holds several overloads of the
same routine. It is what identifies this one, and what a drop has to name.

A **quick filters** switch adds a box over each column of the list, for narrowing what
is already there without asking the server again.

## Keeping the list

**Save** writes the current list as a snapshot and **Open...** brings one back.

## Related

- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/),
  which reports the stored procedures a change would affect.
