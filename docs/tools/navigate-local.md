---
title: Navigate Local
layout: default
parent: Navigate
nav_order: 2
permalink: /tools/navigate-local/
---

# Navigate Local
{: .no_toc }

The same browser, over a project folder on this machine, with one addition that
matters: a local source can be built on the server without going back by hand.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Navigate Local**.

**Browse...** picks the project folder, and the box also remembers the paths you have
used before. The folder name on the filter bar is clickable: it reveals the folder in
the file explorer.

## The filter panel

| Filter | Default | What it does |
|---|---|---|
| **Subfolders** | `Q*` | Which subfolders to look in. They stand for the source files, so `Q*` covers the usual naming |
| **File** | `*` | The file name. Wildcards allowed, such as `MY*` or `*ORD*` |
| **Type** | `*` | The source type, taken from the file extension: RPGLE, CLLE, SQLRPGLE |
| **Text** | `*` | Searches the description recorded in the project metadata |
| **Last changed** between two moments | off | Tick the box to use it |

**Find** reads the folder again and applies the criteria. The fold arrow collapses the
panel and the criteria are summarized on the status bar, as on the server side.

**Open mode** (edit or read-only) and the **quick filters** under the column headings
work the same way too.

## The metadata, and why it matters

**Create .ibmi** creates the folder that records each source's description, type and
dates.

Without it a folder is just files: an upload cannot restore a description, and a
comparison has nothing to compare but content. With it, the sources can travel back
carrying what they had.

## Project Properties

The project carries its own libraries, written into the project's own properties file:

| Control | What it does |
|---|---|
| **Source library** | The library these sources mirror: where they came from, and where Upload puts them back |
| **Compile library** | Where Run Action leaves what it builds. Empty means the same as the source library |
| **Library list** | The libraries a compile needs, in order, separated by spaces |
| **Save** | Writes the values into the project |
| **Apply** / **Load** | Put them on the connection, or read back what the connection is using |
| **Refresh** | Reads the file again, discarding anything unsaved, and asks first |
| **Open raw file** | Opens the properties file in the editor. Saving it refreshes this section |
| **Send to Server** | Writes this project's compile library and library list into the source library on the server, where everyone browsing that library sees them |
| **Get from Server** | Reads them back from the library, so you can see what the team uses |
| **Project Commands** | The commands that prepare the project on the server before a build can run |

An entry can be a named value resolved per developer, which is what lets one shared
project suit everybody.

## The right-click menu

| Entry | |
|---|---|
| **Open** | In the mode the radio says |
| **New source...** | In this project |
| **Run Action on Server...** | Stages the source into the library the project names and runs your own action against it |
| **Upload to Server (replace)...** | Straight back over the member it mirrors |
| **Copy...** | Within the project |
| **Copy Name** | **File Name**, or **Name and Path** |
| **Reveal in File Explorer** | |
| **Select for Compare**, **Compare with** | **Active file**, **IFS file...**, **Local file...**, **Member...**, or **Selected** |
| **Delete...** | |

With several rows selected the menu offers the set operations: upload, delete and copy
the names. **Compare Selection** appears at exactly two rows.

## Run Action on Server

This is the reason to work in a folder without paying for it.

The source is staged into the library the project names, and your own Code for IBM i
action runs against it. The staging goes either into the real source file or into a
temporary one that is cleaned up afterwards, whichever you set in the settings.

Compile errors land in the **Problems** panel, on the local file, so the edit, compile,
fix loop stays where you are editing.

## Related

- [Navigate Server]({{ site.baseurl }}/tools/navigate-server/)
- [Upload Local Project]({{ site.baseurl }}/tools/upload-local-project/)
- [Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/)
