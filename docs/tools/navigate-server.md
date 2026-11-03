---
title: Navigate Server
layout: default
parent: Navigate
nav_order: 1
permalink: /tools/navigate-server/
---

# Navigate Server
{: .no_toc }

Libraries, objects and source members in a table you can filter, sort and act on,
instead of a list you page through.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Navigate Server**. It needs an active
connection.

## The filter panel

The top of the panel is the criteria, and **Find** asks the server for what matches
them. You give it a target (a library, a source file, a member or an object) and
narrow it from there:

| Filter | What it does |
|---|---|
| Name | The object, member or library name. Wildcards allowed |
| Type and attribute | `*PGM`, `*FILE`, `RPGLE`, `PF`, and so on |
| Description | The text the object carries. Wildcards allowed |
| **Created** between two moments | Tick the box to use it, then set either end or both |
| **Last changed** between two moments | The same, on the change date |

The **fold** arrow collapses the whole panel once a search is running. The criteria
stay in force, and they are summarized on the status bar, so a folded panel never
leaves you guessing what you are looking at.

Two more controls sit beside it:

- **Open mode**, read-only or edit, which decides how a member opens when you
  double-click it. A protected library always opens read-only whatever this says.
- **Quick filters**, the one-line boxes under each column heading, for narrowing what
  is already on screen without asking the server again.

## The result table

| Column | |
|---|---|
| **Name** | The member, object or library |
| **Type** | `*PGM`, `*FILE`, `*SRVPGM`, and so on |
| **Attribute** | `RPGLE`, `PF`, `LF`, `CLLE`, `SQLRPGLE` |
| **Description** | The text |
| **Last modified** and **Created** | The two dates |
| **File** and **Library** | Where it lives |

Columns sort and resize. **Export** writes the rows currently shown, with the filters
applied, to a CSV file.

**New source...** creates a member, with the library and source file already filled in
from where you are. It is offered on the Member target only: an object or a library is
not created this way.

## Project Properties, for a library

When you browse a library, a section of its own carries the libraries a piece of work
belongs to, read from and written to `PROJECT.PROPERTIES` in that library:

| Control | What it does |
|---|---|
| **Source library** | The library you are browsing. Not editable: it is what it is |
| **Compile library** | Where Run Action leaves its objects. Empty means build where the source lives |
| **Library list** | The libraries a build needs, in order, separated by spaces |
| **Save** | Writes these values into the library |
| **Apply** | Puts them on the connection: compile library as current library, this list as the user portion. It replaces the list in force |
| **Load** | Fills the box with the list the connection is using now. Nothing is saved until you press Save |
| **Refresh** | Reads the properties again in case somebody else changed them. Anything unsaved is discarded, and it asks first |
| **Open raw file** | Opens the properties member in the editor. Saving it refreshes this section |
| **Project Commands** | The commands that prepare this library before a build can run. Opens the list to edit and to run |

Because the properties live **in the library**, the whole team picks up the same ones.

## The right-click menu

The menu is built for the row you are on, so it is short and it is relevant. Entries
with an arrow are groups: clicking the group itself runs the option you nearly always
want, and the arrow opens the rest.

### On a source member

| Entry | |
|---|---|
| **Open** | In the mode the radio says |
| **New source...** | In the same source file |
| **Run Action...** | Your own Code for IBM i action |
| **Copy...** | To another library or source file |
| **Copy Name** | Name, or **Name and Location** |
| **Download...** | **Member**, **File to Member**, or **Library to File to Member**, which is the folder depth you get |
| **Generate Metadata** | The descriptions, types and dates that let the sources be sent back later |
| **Upload and Replace...** | Straight back over the member it came from |
| **Select for Compare** | Marks this one as the left-hand side |
| **Compare with** | **Active file**, **IFS file...**, **Local file...**, **Member...**, or **Selected** |
| **Delete...** | With a confirmation |

### On a library

| Entry | |
|---|---|
| **Navigate** | **Sources** or **Objects** |
| **Download** | **Sources**, and **Generate Metadata** |
| **Objects References** | A heading over **Programs Level Check Analyzer**, **Native Query Level Check Analyzer**, **Programs Signatures Analyzer**, **Library Compile Order** and **Object and Sources**, each opened for this library |
| **Sync with** | **Library...** or **Local Project...** |
| **Save library to SavF...**, **SavF Manager** | |
| **Add Library to LibL** | |
| **Copy Name**, **Delete...** | |

### On an object, by what the object is

The menu adds the entries that make sense for that type, which is what saves the trip
to another panel:

| Object | What the menu offers |
|---|---|
| `*FILE` | **File Viewer**, **Journal entries**, **See Sources** |
| `*BNDDIR` | **Edit Binding Directory**, **Compare Binding Directory...** |
| `*MSGF` | **Edit Message File**, **Download messages...** |
| `*JOBD` | **Job Description Info** |
| `*MSGQ` | **Message Queue Viewer** |
| `*USRPRF` | **User Info** |
| `*OUTQ` | **List Spooled Files** |
| `*QRYDFN` | **Native Query Info**, **Native Query Level Check Analyzer** |
| `*SRVPGM` | **Programs Signatures Analyzer**, **Procedure Change Impact Analysis** |
| `*SAVF` | **Display saved objects**, **SavF Manager** |
| Any | **Show info**, **Object Change Impact Analysis**, **Copy to Library...**, **Save to SavF...**, **Copy Name** (**Object** or **Library/Object**), **Delete...** |

### With several rows selected

Select with Ctrl and Shift, and the menu changes to the ones that make sense for a set:
**Copy Names**, **Download** with the same three depths, **Generate Metadata**, **Copy
to Library...**, **Save to SavF...**, **Delete...**.

**Compare Selection** appears at **exactly two** rows, and compares them with each
other.

### Wherever it opens

A menu near the bottom or the right of the window stays on screen, measured as it opens
so that a long option counts for its real width.

## Related

- [Navigate Local]({{ site.baseurl }}/tools/navigate-local/), the same browser over a
  folder on this machine.
- [Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/), for sending the
  work back.
