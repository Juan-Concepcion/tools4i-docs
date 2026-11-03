---
title: Dump Files Viewer
layout: default
parent: Spooled files
nav_order: 2
permalink: /tools/dump-files-viewer/
---

# Dump Files Viewer
{: .no_toc }

A program dump read as sections and tabs instead of as ninety pages of printout, with
the source of the failing program opened beside it.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Dump Files Viewer**, then **Import dump
file**: a program dump previously saved from a spooled file. It is broken into
readable sections.

No connection is needed to read a dump you already have, which is what makes this
useful when somebody sends you the evidence instead of the access.

## The five tabs

| Tab | What it holds |
|---|---|
| **Details** | The dump's own sections: program status, the statement that failed, the call stack and the rest |
| **Files** | The files the program had open, with their state at the moment of the dump |
| **Indicators** | Every indicator and its value when the program failed |
| **Variables** | The program's variables and the values they held |
| **Raw dump** | The dump exactly as it came, unparsed. Where to look when a section is not recognized |

Every tab has its own search, where **Enter** goes to the next match and
**Shift+Enter** to the previous, and the first four have **Expand all** and **Collapse
all**. On a dump of any size, collapsing everything and opening one section is how it
becomes readable.

Two filters earn their place:

- **Indicators that are on**, which turns a wall of `0` into the handful that matter.
- **Hide defaults** on Variables, which drops the ones still holding their initial
  value.

## The source, at the statement it stopped on

**Open source** opens the source of the program that failed, positioned on the
statement where it stopped. It resolves from the server or from a local project open
in [Navigate Local]({{ site.baseurl }}/tools/navigate-local/), so it works whichever
way you keep your sources.

The dump and the code that produced it end up side by side, which is the whole point.

## A record buffer as fields

On the **Files** tab, a record buffer can be read as the file's own fields rather than
as a block of bytes. The value that was wrong is usually in a field, not at an offset.

**Close** goes back from the fields to the dump.

Each file the program had open can also be opened in the
[File Viewer]({{ site.baseurl }}/tools/file-viewer/) from here, so "what is actually
in that record now" is one click rather than a new investigation.

## Related

- [File Viewer]({{ site.baseurl }}/tools/file-viewer/)
- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
