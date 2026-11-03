---
title: From the editor
layout: default
nav_order: 17
permalink: /tools/from-the-editor/
---

# From the editor
{: .no_toc }

Five entries Tools4i adds to the editor's own right-click menu, so the source you are
reading can answer its own questions without a trip to a panel.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Where they appear

Open a source and right-click in the text. The Tools4i entries sit together in their
own group, and **each one appears only when it applies**:

| Entry | Appears when |
|---|---|
| **Extract SQL to Run** | The source is RPG or CL |
| **Copy Source to Location...** | The file open is a source member on the server |
| **Download Source to Local Project...** | The same |
| **File Viewer** | The same |
| **Open Referenced Object Source** | Something is selected in the editor |

So a local file shows fewer entries than a member, and the submenu for a referenced
object only turns up once you have selected a name. Nothing is offered that would fail
if you clicked it.

## Extract SQL to Run

An RPG or CL program that builds its query in pieces, line by line, is readable only
by the compiler. This turns it back into a statement.

**Select the lines** where the source assembles the query and the statement opens as
SQL, ready to run, with the values the program supplies left as **markers to fill
in**. Every line of the result says which source line it came from, so a statement
assembled from fourteen places can still be traced back.

**With nothing selected**, an RPG source offers the statements it holds, written out
in full. That is the fastest way to see what a program really sends to the database.

The point is comprehension, not execution: what you get is a statement you can read,
run, and explain to somebody.

## Copy Source to Location...

Copies the member you are reading to another library or source file, without going
back to a browser to find it again.

## Download Source to Local Project...

Brings the member into a local project folder, with the metadata that lets it be sent
back later.

## File Viewer

Opens [File Viewer]({{ site.baseurl }}/tools/file-viewer/) from the source you are
reading, which is the jump from the code to the data it works on.

## Open Referenced Object Source

Select a program name, a copybook name or an object name in the code, and the submenu
offers two places to look for its source:

| Entry | Where it looks |
|---|---|
| **From Server** | Resolved in library-list order, which means **the same member the compiler would take** |
| **From Local** | In the project folder open in [Navigate Local]({{ site.baseurl }}/tools/navigate-local/) |

The library-list rule is the valuable part. On a system with four copies of the same
program in four libraries, "which one is this call actually reaching" is a question
the editor can now answer by opening it.

## Related

- [Navigate Server]({{ site.baseurl }}/tools/navigate-server/)
- [Navigate Local]({{ site.baseurl }}/tools/navigate-local/)
- [File Viewer]({{ site.baseurl }}/tools/file-viewer/)
