---
title: Tools4i Settings
layout: default
parent: Settings
nav_order: 1
permalink: /tools/tools4i-settings/
---

# Tools4i Settings
{: .no_toc }

Every setting the extension contributes, in one searchable form: 79 of them across 15
sections. This page goes through all of them, section by section.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## How the page works

**Tools4i** in the Activity Bar, then **Tools4i Settings**. The same settings are also
in the VS Code settings editor, filtered to this extension.

- The **search** box shows only the settings matching what you type, looking in the
  label, the description and the setting key, so a key quoted in a bug report finds
  its control.
- **Nothing is saved until you press Save.**
- **Reload** reads the settings again and discards anything changed here but not
  saved.
- Each section has **Restore defaults** of its own. It puts that section back to what
  Tools4i ships with **and keeps it following later improvements** to those defaults,
  instead of freezing it at today's values. Names you chose by hand are left alone.
- A list setting (libraries, environments, patterns) can be filled from a file rather
  than typed.

---

## Startup

| Setting | What it does | Default |
|---|---|---|
| **Restore Panels** | Reopens the Tools4i panels that were open when VS Code closed. Most come back **empty**: every panel is a live view over a connection, and the library, file or job that was in it is not recorded anywhere a restore could read | off |
| **Open View** | Opens the Tools4i view in the Activity Bar at startup, whether or not it was open when you closed. Off, VS Code decides | off |

## Duplicate Spooled File

| Setting | What it does | Default |
|---|---|---|
| **Mode** | How copying a spooled file works. **Off**, the copy options only point back at this setting. **Command** calls a command you already have. **Program** deploys and calls a small program for it | off |
| **Deploy Library** | Where the program-mode helper is compiled on first use. Blank uses Code for IBM i's temporary library; a named library keeps it across sessions, and you need authority to create it there | `ILEDITOR` |
| **Library** | For command mode: the library holding the duplicate command | `TAATOOL` |
| **Command** | The command name in that library | `DUPSPLF` |

The default of **off** is deliberate: nothing is created on your system, and nothing
is called, until you have said which of the two ways your shop uses.

## Library Compile Order

These four teach the analyzer your shop's naming, which is how it works out what a
member builds and what it depends on.

| Setting | What it does | Default |
|---|---|---|
| **Module Suffix** | The suffix that marks an ILE module source or object | `M` |
| **Service Program Suffix** | The suffix that marks a service program. A service program is paired with the module it is built from through these two | `B` |
| **Prototype Suffix** | The suffix that marks a prototype copybook, a member named like a module but ending in this | `P` |
| **Copybook Marker** | Text in a member's **description** that marks it as a copybook, never compiled and left out of the order. Case-insensitive; blank disables it | `COPYBOOK` |

If your shop names things differently, these are the first four settings to change:
the compile order is only as good as the naming it is told about.

## Scan Server Sources

| Setting | What it does | Default |
|---|---|---|
| **Default Engine** | Which way a search starts: **Unix Search**, which reads the members as text and allows every option, or **IBM i Native Search**, which has the server search its own source. Changeable per search from the panel | Unix Search |
| **Max Result Lines** | The most matched lines one search brings back. A very common term over a large library matches almost every line of every member; on reaching this the search stops collecting and keeps what it has | 200,000 |

## Compile Local Source

How **Run Action on Server** puts a local source on the server before running your
action. Both routes stage it into the library the project names.

| Setting | What it does | Default |
|---|---|---|
| **Default Route** | **Member**, straight into the real source file, or **Temporary source**, into a scratch file | member |
| **Source File** | The target source file for the member route. Blank uses the local subfolder name, such as `QRPGLESRC` | blank |
| **Temporary Source File** | The file used by the temporary route. It is created in the compile library when missing, sized to fit the source, and **never deleted**: only the staged member is removed | `QTMPSRC` |
| **Remove Temporary Source** | Removes the staged member after compiling. On by default, because that route exists to leave nothing behind. Turn it off to inspect exactly what was compiled | on |
| **Divergence Check** | Before the member route replaces an existing member, compares it with the local file and warns when the server copy is newer. Does not apply to the temporary route, which never touches the real source | on |
| **Diagnostics** | Where compile errors are shown: **own** (needs the action to ask for the event file), **Code for IBM i**, or **off** | own |
| **Diagnostics Timeout** | How long to wait for Code for IBM i's own errors when the listing could not be read directly | 4000 ms |
| **Library List Check** | Before compiling, compares the project's library list with the connection's and offers to apply it when they differ | off |
| **Keep Staged Source** | Kept only so a value left by an older version can be cleared. The temporary route decides through **Remove Temporary Source** | on |

## Object and Sources

The first two are the defaults of the panel's own fields; the rest are its skip rules,
each a switch and a list.

| Setting | What it does | Default |
|---|---|---|
| **Source Files** | The default source-file filter. Blank analyzes `Q*` | blank |
| **Outside Search** | Looks for a counterpart outside the listed libraries, across the rest of the server | off |
| **Skip: Library/File/Member matches** | Patterns to skip, comma-separated, `*` anywhere. A two-part pattern assumes any library | on, `*/QSRVSRC/*P, */QFMTSRC/*, */QTESTSRC/*` |
| **Skip: Description contains** | A member whose description contains any of these is skipped | on, `COPYBOOK, CPYBOOK` |
| **Skip: Source attribute in** | Types that never build an object of their own | on, `*INC, *CPY, TXT` |
| **Skip: Object type in** | Object types left out. They are still listed under Skipped Objects | on, every type that never has a source member |
| **Skip: Owner in** | Profiles whose objects to skip, handy for IBM-supplied ones | off, blank |
| **Skip: Library in** | Library patterns to skip | off, blank |

Everything skipped is still listed, under **Skipped Sources** and **Skipped Objects**,
so a rule can never hide something without saying so.

## Review Authority Failures

| Setting | What it does | Default |
|---|---|---|
| **Exclude Users** | The current users left out of the result: the service profiles that fail authority checks all day. Editable per run in the panel | `QTMHHTTP` |

## Data Model

Twenty settings, in two groups on the page.

### The model itself

| Setting | What it does | Default |
|---|---|---|
| **Folder** | Where the model file is stored and loaded from. Blank uses your home folder | blank |
| **Native Read Strategy** | How the Extractor reads native source members: **download** or **SQL**. Both give the same result and differ only in speed | download |
| **Server Path** | The directory on the IBM i where the model is published and retrieved by **Push to Server** and **Pull from Server** | `/tools4i/datamodel` |
| **Default Layout** | The arrangement the Viewer starts with and **Re-layout** uses. Seven to choose from, including two directed ones, concentric, grid and circle | cose |

### The confidence of an implied foreign key

Four thresholds, read against the percentage of rows that match when a candidate is
confirmed against the data:

| Setting | Meaning | Default |
|---|---|---|
| **High Match** | High confidence at or above this, below 100%. **100% is always Very High** | 95 |
| **Medium Match** | Medium at or above this | 80 |
| **Low Match** | Low at or above this | 50 |
| **Very Low Match** | Very low at or above this. Below it, none | 20 |

### Colors and shapes

Six item types, each with a **fill color** and a **shape**: table (SQL tables and
physical files), logical file, view, index, materialized query table, and other.

Colors take any CSS color and ship as a colorblind-safe set; shapes come from a list
of seventeen, from rectangles and ellipses to hexagons, barrels and stars. The
defaults are a rounded rectangle for tables, a rounded hexagon for logicals, an
ellipse for views, a rounded diamond for indexes and a barrel for materialized query
tables.

What you set here is what the diagram draws, and what its legend and its exports
show.

### Sensitivity

| Setting | What it does | Default |
|---|---|---|
| **NPI Name Patterns** | Column-name fragments of **your own** database that must be classified as nonpublic personal information, for the Dictionary's scan to find alongside the built-in ones | empty |
| **PII Name Patterns** | The same, for personally identifying information: name, address, phone, email, date of birth | empty |

## Local Project

| Setting | What it does | Default |
|---|---|---|
| **Apply Library List On Open** | Puts a project's library list on the connection as soon as the project is on screen in Navigate Local. **Off by default**: opening a project to look at it should not change the job you are working in | off |
| **Set Current Library** | When the project libraries are applied, also points the current library at the compile library, so unqualified names find this project's objects first | off |

## Server Library Project

| Setting | What it does | Default |
|---|---|---|
| **Properties File** | The source file in a library that holds its properties, a file of its own rather than one shared with the sources | `IBMI` |
| **Apply Library List On Find** | When Find runs against a single library, puts that library's own list on the connection. Off by default, for the same reason as above | off |
| **Set Current Library** | Points the current library at that library's compile library when its properties are applied | off |

## Diagnostics

What goes into the Tools4i output channel. Each logged call records its duration, its
row count or return code, and any error.

| Setting | What it does | Default |
|---|---|---|
| **Level** | **Off**, **errors** only, or **all** calls | all |
| **Categories** | Which kinds of server interaction to log: SQL, commands, shell. Unticking one stops logging it entirely | all three |
| **Log Input** | Includes the statement or command text in each entry. **Off by default**: turn it on while troubleshooting | off |
| **Log Output** | Includes the rows or the output, capped by the limit below | off |
| **Max Output Chars** | How much output is kept per call before it is truncated. 0 means no limit | 4000 |
| **Only Tools4i** | Logs only the calls Tools4i itself makes. All IBM i extensions share one connection, so without this the channel also records the language server resolving copybooks, the debugger and Code for IBM i's own housekeeping | on |
| **Log Actions** | Records each **user action**: which panel it came from and which button or menu option was used, with a short summary of the target. Useful when supporting a ticket | off |

A note on **Only Tools4i**: a call whose origin cannot be told apart is **kept**
rather than dropped, on the grounds that losing your own entries is worse. So the
channel can still show traffic that is not Tools4i's, and the action lines are the
reliable marker of what came from here.

## PDF creation

| Setting | What it does | Default |
|---|---|---|
| **GhostPCL Path** | The full path to the local GhostPCL executable used to convert printer-format spooled files to PDF when downloading them. It is part of the Ghostscript family; the plain interpreter cannot read that format | blank |

## System Protection

| Setting | What it does | Default |
|---|---|---|
| **Protected Libraries** | Libraries this extension must **never modify**. Exact names and `*` wildcards, matched case-insensitively | empty |

Inside a protected library the extension blocks its own copy, rename, delete and
change-text, its deploys, its sync writes and its editor saves, and source members
open read-only.

This is the cheapest insurance in the product. Put production in it before you do
anything else.

## Production Protection

| Setting | What it does | Default |
|---|---|---|
| **Enabled** | Turns it on. Any connection whose host name or IP is **not** listed below is treated as production | off |
| **Development Environments** | Your **development** systems, one entry each, as the host name or IP the connection uses | empty |
| **Block Destructive** | On production, blocks delete, rename and change-text of objects, libraries and members | on |
| **Block Create** | Blocks creating objects and libraries by copy. Not destructive, but it still adds objects to a production system | on |
| **Block Uploads and Sync** | Blocks uploads from local, and every sync write | on |
| **Block Editor Saves and Deploys** | Blocks the message file and binding directory editors from saving, and the spooled-file helper from being deployed | on |
| **Force Members Read Only** | Opens all source members read-only. Best effort: the actual saving is handled by Code for IBM i | on |

The list is of **development** systems, not production ones, on purpose: a system you
forget to list is treated as production, which is the safe way for the mistake to go.

## Related

- [About Tools4i]({{ site.baseurl }}/tools/about-tools4i/)
