<img src="media/icon.png" alt="" width="96" align="right">

# Tools4i

**English** · [Español](README.es.md)

IBM i developer tools for Visual Studio Code, built on top of
[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi).

Tools4i adds a set of tools for the tasks that come up during the day: finding
objects and source, searching inside the code, looking at the data, modelling and
documenting the database, managing jobs and spooled files, editing IBM i objects,
and analysing what a change might affect. All of it from the editor, and against
the server.

**Install it:**
[VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i)
·
[Open VSX](https://open-vsx.org/extension/tools4i/tools4i)
(which is also how it reaches IBM Bob, IBM's own build of VS Code)

> **About this repository.** This is the public home of the Tools4i
> documentation: what the extension does, how to install it, what changed in each
> version, and where to report a problem. The extension's source code is not
> published here. Bug reports and ideas are welcome in
> [Issues](https://github.com/Juan-Concepcion/tools4i-docs/issues).

## Requirements

- **Visual Studio Code 1.118 or later**, or an IBM Bob built on that version or a
  newer one. The Bob 2.1 line is.
- **[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)**,
  installed automatically as a required dependency.
- **An active connection** to your IBM i. Tools4i works through the connection
  Code for IBM i already has; it never opens one of its own.

Full instructions, including the offline case and how to update or remove it, are
in [INSTALLATION.md](INSTALLATION.md).

## Getting started

1. Install **Code for IBM i** (it arrives automatically as a dependency) and
   connect to your system.
2. Open the **Tools4i** view from the Activity Bar, or run any command from the
   Command Palette (**F1**, then type the tool name).

## Features

Every tool below opens from the **Tools4i** view in the Activity Bar, or from the
Command Palette by name. The headings match the groups in that view. Click the
star on a tool to keep it in a **Favorites** section at the top of the view; it
stays listed under its own group as well.

Most result panels share the same habits: per-column quick filters, sortable
columns, CSV export, and, for the analysis and inspection tools, saving what is on
screen as a snapshot you can reopen later, on another machine or with no
connection at all.

### Navigate

- **Navigate Server**: browse libraries, objects and source members. Filter by
  name, type, attribute, description and create or change date, with sortable and
  resizable columns, quick filters and CSV export. Change a description or source
  type, rename, copy or delete, drill from a library into its objects or sources,
  and **create a new source** from the bar or a row's menu, with the library and
  source file already filled in from where you are. From here you can also
  **download sources to a local project**, whether one member, a source file or a
  whole library, choosing how the folders are laid out, together with the metadata
  that lets them be sent back later. Once the sources sit in a folder they are
  within reach of whatever your team uses outside the server: source control and
  versioning, AI-assisted code analysis, or any other product that expects plain
  files rather than members in a library.
- **Navigate Local**: the same browser, with its filters, sortable and resizable
  columns, quick filters, row selection with Ctrl and Shift, and the actions on
  each row, applied to a local project folder of sources instead of the server.
  Select several rows to upload or delete them in one go, edit a name, source type
  or description straight in the table, and create a new source there as well. And
  the sources don't have to travel back by hand to be built: **Run Action on
  Server** stages a local source into the library the project names and runs your
  own Code for IBM i Action against it, either into the real source file or into a
  temporary one that is cleaned up afterwards, whichever you set in the settings.
  Compile errors land in the **Problems** panel on the local file, so the
  edit, compile and fix loop stays where you are editing.
- **Project Properties**: the libraries a piece of work belongs to, kept with the
  work itself. The library its sources mirror, the library a build writes to, and
  the library list a compile needs. A local project keeps them in the folder, and a
  server library keeps them in the library, so a whole team picks them up. **Apply**
  puts them on the connection and **Load** brings back what the connection is
  using, so a list built by hand is kept rather than typed again. A library can be
  named per developer, which lets one shared project suit everybody. **Project
  Commands** holds the list that prepares a project: run them all, resume where the
  last run stopped, and see what each one answered.

### Search

- **Scan Server Sources**: content search across source members of several
  libraries at once, with target and omit lists (wildcards allowed), a column range
  so fixed-format comments don't drown the result, and match modes. Search terms
  are added one at a time and listed as removable chips, each either **Matches** or
  **Does NOT match**, so a multi-term search reads as a list of decisions rather
  than a wall of controls.
- **Two ways to search the server**, picked from the gear beside the options or set
  as your default. **Unix Search** reads the members and offers everything above,
  and **IBM i Native Search** has the server search its own source, several times
  faster over a large library, for one plain-text term. The panel offers only what
  the chosen way supports, so a search always runs as it reads on screen.
- **Scan Local Sources**: the same search over a local project folder.
- **Sources Scan Results**: the results of each scan in its own tab, with the
  members on one side and the matching statements on the other. Order the libraries
  by priority and highlight the lower-priority copies that a first-match rule would
  discard, filter per column, and export. Right-click a tab to **load the criteria
  that produced it** back into Scan Server or Scan Local Sources, or to copy them
  as text. And the option that saves the most time on an old code base: **hide
  matches that fall on commented-out code**, so looking for a field stops returning
  the twenty places where it was commented out years ago.

### Compare and sync

- **Sync Local Project**: compare a local folder against a server library and see,
  member by member, what is in sync, what differs, and what exists on only one
  side. From there send the work done locally up to the server, replacing a member
  or creating one that isn't there yet, bring server changes back down, sync
  descriptions either way, or diff and edit both sides at once. To push a whole
  project in one operation instead of member by member, use **Upload Local
  Project**.
- **Sync Server Library**: compare a newer project library against one or more
  ordered base libraries and reconcile the differences.

### Transfer

- **Upload Local Project**: send a local project back to a library, previewing what
  will be created and what replaced, and narrowing the upload by source file,
  member or type. When the target source file does not exist yet, you decide the
  character set it is created with; and when a character in your source has no
  equivalent on the server, you decide what is written in its place instead of
  finding out afterwards. It also creates or replaces `*BNDDIR` objects from the
  binding directory files the project carries.
- **SavF Manager**: list the save files of a library or of a special value
  (`*ALLUSR`, `*LIBL`, `*CURLIB`, `*ALL`), each with what it holds: number of
  objects, saved libraries, compression, size, owner and last update. Browse the
  objects inside a save file, and restore everything, a library, a set of objects,
  or **one single object into the library you choose**. Save objects or a whole
  library into a save file, append more objects to one that already exists, create,
  clear, delete or copy a save file to another library, and move it between the
  server and your machine in either direction.

### Editors

- **Binding Directory Editor**: a `*BNDDIR` is normally maintained one entry at a
  time, with no way to see the whole picture. Here the full list is on screen at
  once, sortable and filterable: add, edit and remove several entries and commit
  them in a single save, or discard the lot and start again. One pass tells you
  whether every referenced object still exists on the server, and a comparison
  against another binding directory shows what is missing, extra, or bound with a
  different activation. It works against the server or on a binding directory
  downloaded into a project, which the project upload can apply back to a library
  later.
- **Binding Directory Sync**: put two binding directories side by side, a target
  and a base, and see exactly how they differ. Entries the target is missing,
  extras it carries that the base does not, and entries present in both but bound
  with a different type or activation. One action then brings the target in line
  with the base, adding what is missing, removing what is extra and aligning the
  rest, which is what you want when a development binding directory has drifted
  from the one production was built with.
- **Message File Editor**: open a `*MSGF` and view, add and edit its message
  descriptions, with search over ID, first-level text and help.

### Spooled files and dumps

- **Spooled Files Manager**: find spooled files by user, output queue, status, form
  type, user data, job or date-and-time range. View the content, download it as
  text, hold, release, change attributes, copy to another output queue once you
  have said how copying should be done, delete, and jump to the job that produced
  it. It also opens the path to producing a PDF out
  of a spooled file: the transform is performed by the server, or by a third-party
  conversion tool of your choice that you install locally and point the settings at.
- **Dump Files Viewer**: import an ILE program dump (`QPPGMDMP`) and read it as
  details, files, indicators, variables and the raw text, with search and expand or
  collapse. It also opens the source of the program that failed, on the statement
  it stopped at and resolved from its own library or the library list, so the dump
  and the code that produced it sit side by side. A record buffer can be read as
  the file's fields rather than as bytes, and each file the program had open can be
  browsed in the **File Viewer**.

### Jobs

- **Jobs Manager**: filter active and completed jobs by user, name, status or
  subsystem, with per-column quick filters and an optional extra-detail pass (type,
  entry time, resource use). Act on one job or several at once: hold, release, end
  controlled or immediate, change attributes. Jump straight to the job log, the job
  info, its spooled files or the user profile.
- **Job Info**: a single job across ten tabs: attributes, job log, call stack,
  library list, open files, activation groups, locks, definition, file overrides
  and commitment control. Save the whole thing as a snapshot and reopen it later,
  or import a printed job report to study a job with no connection at all, which is
  useful when someone sends you the evidence instead of the access.
- **Job Log Viewer**: a job log as a table you can actually work through, with
  time, message ID, severity, type, the program it came from and the text, colour
  coded by severity. Narrow it down to a time window, filter by message type or
  severity from the values present in that log, or search the text with next and
  previous navigation. Expand the second-level text of one message or of all of
  them at once, and save the log to reopen later, or open one saved earlier, which
  is how you read a job log from a system you are not connected to.
- **Job Description Info**: look up `*JOBD` objects by name and library, with
  wildcards, and read each one's attributes in a grouped grid: the library list a
  job starts with, the job queue and priorities, the output queue, the message
  logging level, and the rest. It is where the answer usually is when the same
  program behaves differently depending on how it was submitted. The result can be
  saved and reopened later.
- **Message Queue Viewer**: browse a message queue filtered by user or originating
  job, expand second-level help, reply to inquiry messages, and clear what has been
  seen while inquiries still unanswered stay protected. A queue can be saved and
  reopened later, which is the simplest way to attach evidence to a ticket.

### Database

- **File Viewer**: physical and logical files, tables, views and indexes, choosing
  the member in a multi-member file and the record format in a multi-format logical
  file. Six tabs:
  - **Data**: the rows, capped to the number you set, filtered per column or with a
    condition built by clicking on the columns, shown by short system name or by
    long name, and exportable to CSV. On a physical file or table you can also
    **add, change and delete records**.
  - **Info** and **Columns/Fields**: the file's own attributes and the definition of
    every field, including its position in the record, filterable and exportable.
  - **Dependents**: the database relations of the file, meaning every logical file,
    view or index built over it, each one with its object type, description and long
    name, so a "who breaks if I change this record format" question is answered
    before the change, not by the compiler afterwards.
  - **RPG Data Structure**: generated in full free, free or fixed format, with or
    without positions, initialised from the data type defaults or from the first
    record, named with the prefix and suffix you choose, ready to paste.
  - **Custom fields**: read a file the way a legacy program reads a
    **program-described file**. Give the layout, meaning name, positions, type and
    decimals, by hand or by importing RPG input specs or a positional data
    structure, and the decoded values come back as a normal grid, exportable to CSV.
- **Journal Entries Viewer**: for a journaled file, data area or data queue, list
  its journal entries and decode each record image into the file's own columns,
  with the before and after images of every update side by side. Narrow the search
  to a member, a date-and-time range, a set of entry types (writes, updates,
  deletes, or whatever codes you need) and a row cap, filter the result, export it
  to CSV, and jump straight to the File Viewer to compare what the journal recorded
  with what the file holds today.
- **Stored Procedures Manager**: filter SQL procedures and functions by schema,
  name, external program, or text inside the definition itself. View the definition
  and parameters, generate a call template, run it, and drop the routine.
- **Native Query Info**: everything a `*QRYDFN` query holds, in four tabs. Its
  attributes, the files it uses with their level-check status, the definition itself
  with selection, sorting and formatting expandable section by section, and the
  **equivalent statement**, ready to copy when the query has to become something a
  modern tool can run. From there you can open the level-check analyzer for that
  library, and save the whole thing to reopen later.
- **Data Area Info**: what a `*DTAARA` holds right now, meaning type, length,
  decimal positions, its value and its description, each field copied with a click.
  Many applications keep their configuration and their run switches in data areas,
  so this is often the difference between a program that is wrong and a program
  that was told to behave that way.

### Data model

Every tool below works on the same copy of the model, and nothing reaches the
model file until you press **Save changes**, from whichever of them you happen to
be in. **Discard** puts everything back the way it was saved.

- **Data Model Extractor**: build a data model from the Db2 catalog, from native
  DDS and SQL sources on the server or on disk, or from a DDL script. Whole
  libraries or a single object, merging or replacing, with the result staged until
  you save it.
- **Data Model Editor**: add items to the model by hand, and edit items, keys,
  relationships and dependencies that no extraction can know about. Group items
  into business processes, and publish the model to the IFS for the team.
- **Implied foreign keys**: find the relationships that were never declared as
  constraints. A table holding every column of another table's key is a candidate,
  rated by confidence. None enters the model on a guess: each is confirmed against
  the catalog or against the data itself, counting the rows that would be left
  orphaned.
- **Data Model Viewer**: this is where **entity-relationship diagrams (ERDs)** are
  built, including the elements particular to IBM i, with physical files, logical
  files and multi-format logical files drawn over the physicals they are built on,
  alongside tables, views and indexes. Add one item, its related items, or a whole
  business process, and the diagram grows around what you are explaining rather
  than showing the entire library. Notes can be pinned to the canvas, and diagrams
  saved, reopened and exported as an image.
- **Data Model Dictionary**: a business glossary at column level. One row per
  distinct column definition, because two columns sharing a name but not a data
  type are two different things, and describing them as one produces a wrong
  glossary. Each row carries its business description, the text the source
  carries, a "used by" cross-reference across the model, a measure of how much is
  documented, and CSV or Markdown export.
- **Personal data classification**: mark which columns hold personal information
  and of what kind, inside the Dictionary. Detection proposes candidates from the
  column name, the source text and the description, but **applies nothing on its
  own**: every proposal goes through a review dialog. It warns when the same column
  name is classified in some files and not in others, under-tagging being the real
  exposure, and when a classification has come loose because the column definition
  changed, so it can be reattached or dropped deliberately.
- **Model health checks**: what a model accumulates over time. Relationships
  pointing at items that are not there, references to items missing from the model,
  duplicated items and duplicated relationships, items nothing connects to, and
  redundant access paths. Each finding jumps to the item it is about.
- **Data Model Comparison**: compare your model against the server now, against
  another model file, or one library against another. Every difference is stated as
  work to do in **your** model, meaning add, remove or update, in four tabs: the
  objects, how they are linked, the processes and the saved diagrams. Objects,
  dependencies, processes and diagrams can be brought across from the panel itself,
  and the change is held unsaved until you save it in the Editor. A process or a
  diagram both models have offers a choice: **replace** it with the other version,
  or **merge** what the other has into yours, keeping everything already there.
  Double-click a row to see the object or dependency in full, with every difference
  marked on it. The **Impact** column says what a change reaches beyond the model:
  a program that may need recompiling, glossary entries that would come loose, and
  the diagrams and processes the object appears in.

### Object references and impact (beta)

Two of these tools are in **beta testing**: Procedure Change Impact Analysis and
Programs Signatures Analyzer. They are usable and in daily use, but their results
should be reviewed before you act on them, and the side bar marks each one as beta
as a reminder.

- **Programs Level Check Analyzer**: programs that will level-check against files
  in your data libraries, in three views. The level-id comparison (with an
  "affected only" filter that also surfaces mismatches where level checking is
  simply turned off), the resulting list of programs to recompile, and the files
  involved. Copy the list or export any view.
- **Native Query Level Check Analyzer**: `*QRYDFN` queries that will fail because a
  file definition changed.
- **Programs Signatures Analyzer**: the callers that will fail at activation
  because the service program they were bound to no longer carries the signature
  they hold, in three views: the comparison, the callers to rebind, and the service
  programs involved.
- **Object Change Impact Analysis**: what a change to an object would break.
  Dependents to recreate, programs to recompile, stored procedures affected, plus
  the rebuild plan in the order it has to be run. Optionally it walks the call graph
  as well, to show who calls the programs that need recompiling.
- **Procedure Change Impact Analysis**: for an exported subprocedure, every module,
  service program and program to recompile, in order. **Confirm in source** reads
  the sources of the objects bound directly to the one that holds the procedure and
  reports which of them name it. A compiled object cannot answer that, so a miss
  means no explicit evidence, never proof it is unused. Optionally it also lists the
  programs that call the impacted ones, for review only.
- **Library Compile Order**: every source member of a library in a dependency-safe
  build order, going from files to modules, then service programs, then programs.
  Open or copy a member's source, or run a compile action on the ones you select.
- **Object & Sources**: reconcile source members against compiled objects. Objects
  with no source, sources with no object, and stale objects, with configurable skip
  rules.

### System and users

- **PTF Status**: individual PTFs or whole PTF groups, filtered by ID or product,
  with their installed status (loaded, applied, superseded) and CSV export.
- **User Info**: look up a user profile by name, or several at once with a wildcard
  and pick from the matches, and read every attribute it carries in a grouped grid.
  Class and special authorities, group profile and supplemental groups, initial
  program and menu, current library, limit capabilities, password and expiration
  state, sign-on attempts and status, storage used, and when it was last used.
  Enough to answer "why can this user do that", or why it cannot, in one place, and
  the result can be saved and reopened later.
- **Review Authority Failures**: authorization-failure entries from the security
  audit journal over a date-and-time range (the last 24 hours by default), with the
  noisy service users excluded, a row cap, drill-in to the authorities held on the
  object that refused the access, and CSV export.

### From the editor

With a source member open, the editor's context menu adds:

- **Extract SQL to Run**: select the lines where an RPG or CL source builds its
  query and the statement opens ready to run, with the values the program supplies
  left as markers to fill in. Every line says which source line it came from. With
  nothing selected, an RPG source offers the statements it holds written out in
  full.
- **Copy Source to Location**: copy the member to another library or source file.
- **Download Source to Local Project**: bring it into a local project folder.
- **File Viewer**: jump from the source to the data.
- **Open Referenced Object Source, from server or from local**: select a program or
  copybook name in the code and open its source, resolved in library-list order
  (the same member the compiler would take) or from the open project.

### Settings and About

- **Tools4i Settings**: every setting this extension contributes, in one searchable
  form.
- **About Tools4i**: version, author, license, and the Code for IBM i build it is
  running on.

## Settings

Run **Tools4i Settings** for a single searchable form covering every setting the
extension contributes: spooled-file duplication, library compile-order naming, how
a local source is staged before **Run Action on Server** and where its compile
errors are shown, object and source reconciliation defaults, diagnostics logging,
PDF creation, data model storage, colours and shapes, and the protections below.
Each section can go back to what Tools4i ships with **Restore defaults**, which
also keeps that section following later improvements to those defaults. The same
settings are available in the VS Code Settings editor by searching for
`@ext:tools4i.tools4i`.

**Protected libraries**: libraries the extension must never modify. Its own copy,
rename, delete, change-text, deploys, sync writes and editor saves are blocked
there, and their source members open read-only.

**Production protection**: any connection whose host name or IP is not in your
list of development systems is treated as production. Destructive changes, object
creation, uploads and sync writes, editor saves and deploys can each be blocked,
and the UI shows a red production warning.

## Privacy and security

Tools4i makes no network connections of its own, carries no telemetry and needs no
account. The only system it talks to is your own IBM i, through the connection
Code for IBM i already holds.

It installs no server component either. One optional feature, switched off until
you turn it on, asks before compiling a 55 line CL program on your system, and
[its source is published here](server/IUDUPSP3.clle) so nobody has to take that
on trust. A setting switches that feature to a mode that compiles nothing, or
turns it off altogether, and on production the deploy is blocked by default.

The details are in [SECURITY.md](SECURITY.md).

## Support

- **Something broken, or an idea?**
  [Open an issue](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose).
- **Prefer email?** tools4i.support@gmail.com
- **Want to help?** [CONTRIBUTING.md](CONTRIBUTING.md) says what is most useful,
  from a good bug report to fixing these pages.

## Credits

**Juan J. Concepcion**, author and maintainer.

Tools4i stands on work done by others:

- **[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)**
  and everyone who has contributed to it. Tools4i is built on top of it and depends
  on it; it extends that work rather than replacing it.
- **Cytoscape.js** and **Dagre**, which draw and lay out the data model diagrams.
  Every bundled component and its licence is listed in
  [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

Thanks as well to the IBM i developers whose day-to-day work decided what got
built: each tool here started as a task someone was doing the slow way.

## License

MIT. See [LICENSE](LICENSE). The same licence file travels inside the extension
package.
