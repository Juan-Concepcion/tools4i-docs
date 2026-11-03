---
title: Spooled Files Manager
layout: default
parent: Spooled files
nav_order: 1
permalink: /tools/spooled-files-manager/
---

# Spooled Files Manager
{: .no_toc }

Finding printed output by any of the things you actually remember about it, and doing
something with it once found.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Spooled Files Manager**.

## The filters

| Filter | Default | What it takes |
|---|---|---|
| **User** | `*CURRENT` | The owner. `*CURRENT` is the connected user, `*ALL` is everybody |
| **Output queue** | any | Library and name |
| **Status** | `*ALL` | Only the files in that status |
| **Job** | any | `number/user/name` |
| **User data** | any | The tag the program set |
| **Form type** | `*ALL` | |
| **Created** between two moments | off | Tick the box to use it |

The combination that works most often is user plus a time window. **Find** runs it,
and the filter block folds away once the list is up. A **quick filters** switch adds a
box over each column for narrowing what is already on screen.

The **download folder** beside them is where downloaded text and PDF files are saved.

## The right-click menu

| Entry | What it does |
|---|---|
| **Open (view content)** | Reads the spooled file in the editor |
| **Download as text** | To the download folder |
| **Download as PDF...** | See below |
| **Hold**, **Release**, **Delete** | On one file or on a selection, with the count in the label |
| **Change...** | The dialog below |
| **Open job in Jobs Manager**, **Job info** | The job that produced it |

A file held in `*USERASCII` cannot be read or downloaded as plain text, and the menu
says so in the entry itself rather than failing after you click it.

## Change

The dialog changes only what you fill in; anything left blank keeps its current value:

| Field | |
|---|---|
| **Output queue** | Library and name, to move the file |
| **Copies** | 1 to 255 |
| **Form type** | |
| **Priority** | 1 (highest) to 9 |

It applies to every selected file at once.

## Copying to another output queue

Copying works once you have said **how** copying should be done, which is a setting.
It starts switched off, and the copy options point back at the setting rather than
doing something you did not choose.

Two ways, and the choice is yours: call a duplicate command your shop already has, or
let Tools4i deploy a small program for it, which it names, with its library, and asks
about before creating anything.

## Getting a PDF

The transform is done by the server, or by a third-party conversion tool that you
install locally and point the settings at. Both paths are offered; neither is assumed.

## Related

- [Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/)
- [Dump Files Viewer]({{ site.baseurl }}/tools/dump-files-viewer/)
