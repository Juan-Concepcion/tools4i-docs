# Changelog

All notable changes to Tools4i are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and the project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Every version requires the
[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)
extension and an active connection.

## [1.2.8] - 2026-09-19

### Added
- **Duplicating a spooled file starts switched off**, and the copy options say so
  and take you to the setting that decides how it should be done.
- **Duplicating a spooled file asks before creating the program it uses**, naming
  it and the library it goes in.
- **The extension page links to this repository**, where the source of that
  program is published for anyone to read.

### Fixed
- **Copying a spooled file works with older duplicate commands too**, and the
  message says when the copies keep their original owner.
- **A copy that cannot be made gives you the reason in one line**, with the whole
  job log still in the Tools4i output.
- **The Spooled Files setting names the program Tools4i creates**, the same name
  this repository publishes.

## [1.2.7] - 2026-09-17

### Added
- **Restore defaults, section by section.** Each section of Tools Settings can go
  back to what Tools4i ships, today and after every update.

### Fixed
- **A library list survives Load and Apply.** Load copies what the connection
  holds, and Apply puts it on the job exactly as written, `QTEMP` and the
  project's own library included.
- **Find applies a library list without stopping to ask.** Anything left out is
  said in passing.
- **A project's libraries apply to the project you come back to**, not only to one
  you switch to.
- **Implied foreign key candidates belong to the model they were found in.**
  Change model, or extract over one, and the list starts again for what is on
  screen.
- **Downloading a printer file as PDF says what it needs first**, before asking
  where to save it, and offers to set it.
- **Settings save right after an update.** Tools Settings offers to reload the
  window as soon as it sees settings the window has yet to learn, and saves
  everything else in the meantime.
- **Your settings hold what you chose.** Saving writes what you changed, so a
  setting left as it comes keeps following Tools4i, improvements to it included.
- **Every setting does what it describes**, in Object & Sources, Spooled Files and
  the Data Model.

### Changed
- **The member route keeps the source it stages.** There the member is the source,
  so keeping it is no longer a setting. The temporary source route still chooses,
  through **Remove Temporary Source**.

## [1.2.6] - 2026-09-16

### Added
- **Extract SQL to Run: the query a program builds, ready to run.** Select the
  lines that assemble it and the statement opens ready to run, with the values the
  program supplies left as markers to fill in.
  - **Every line says which source line it came from**, so the statement reads
    straight against the program it came out of.
  - **RPG and CL, fixed format or free.** With nothing selected, an RPG source
    offers the statements it holds written out in full.
- **A project and a library carry their own libraries.**
  - **Navigate Local, Project Properties** holds the source library, the library a
    build writes to, and the library list it needs, with **Apply** and **Load**.
  - **A project library can be named instead of fixed**, so a shared project suits
    each developer.
  - **Compile on Server builds into the project's own library**, and can put its
    libraries in force first.
  - **Navigate Server: a library carries its own properties too**, kept in the
    library so the whole team sees them.
  - **Run Action can build into another library**, from a copy of the member that
    keeps its own name, with the errors still on the source you are editing.
  - **Project Commands, the list that prepares a project.** Run them all, resume
    where the last run stopped, or try one on its own.
  - **Server Sync: a project and its library swap properties**, either way, from
    **Actions**.
  - **Open the properties as they are stored**, and the section follows what you
    edit by hand. It says what it cannot use when the file is edited by hand: an
    unknown entry, one written twice, or a line it cannot read.
  - **Applying a library list checks the libraries are there first**, and says
    which are not. The current library is left alone unless you ask for it.
- **Navigate Server and Navigate Local: create a new source**, from the bar or a
  row's menu. The source file or folder is offered if it isn't there yet, and the
  new source opens ready to write.
- **Tools Settings**
  - **A list can be read from a file.** **Import** fills it from a spreadsheet or a
    text file.
  - **Every section folds**, and a search still reaches inside.
- **Data Model**
  - **Query definitions come into the model**, each an item of its own: what it
    reads, what it writes, and drawable on a diagram.
  - **Correct the columns of a relationship you added.** Relationship Info offers
    **Edit columns**: add a pair, drop one, change a side or reorder them.
  - **Items excluded**, a tab in the Extractor and the Editor for what you have set
    aside.
  - **Exclude sits beside Delete.** Exclude keeps an item out of every extraction;
    Delete just removes it, so the next one brings it back.
  - **A missing referenced item can be fetched from the server**, from the list
    itself.
  - **The unsaved marker opens a summary of what is waiting.** Click **Unsaved
    changes** in any panel to see what Save would keep and Discard would undo, as a
    list of counts by part of the model, dictionary and classifications included.
    Open the part you want, or expand them all.
  - **Data Model Viewer: opening a saved diagram shows the list**, with when each
    was saved and how much it holds, with the usual sorting and filters.
  - **Data Model Viewer: the type filters fold into one Item Types button**,
    freeing the toolbar. It carries the count while any type is hidden.
  - **Data Model Comparison: queries are compared when you ask for them.**
- **Object & Sources**
  - **Copybooks and test sources are set aside by default**, so the comparison
    keeps to what builds an object. Two skip rules on screen, yours to clear.
  - **The source attribute rule takes wildcards**, so one entry covers a whole
    family of copybook types.
  - **The count line says what was read and what the skip rules leave in view**,
    and follows the rules as you change them.
  - **Rows kept out of the comparison read as set aside rather than as a problem**,
    each with its reason in its own column.
- **Upload Local Project**
  - **Quick filters on both tables**, with the count saying how many of the total
    are showing.
  - **Two local sources that are one member are marked**, here and in Navigate
    Local: names in one folder differing only by extension are the same member on
    the server.
- **Dump**
  - **Every source it opens asks where from**: program source, file definition and
    buffer layout, from the server or a local project. A layout read locally needs
    no connection.
  - **Each file has its own Open source**, for the definition it was built from.

### Changed
- **Transfer follows the project's properties.**
  - **Uploading a project offers the library its properties name**, resolving a
    library named per developer rather than the one it was downloaded from.
  - **Downloading a library records it with the project**, so the project arrives
    configured.
  - **Sync Local Project fills the library from the folder you choose.**
- **Navigate Local**
  - **A tab is named after its project**, so several open at once tell each other
    apart.
  - **Copying a source starts beside the original**, ready for a variant next to it
    or the matching subfolder of another project.
- **Data Model**
  - **The health tab keeps two questions apart**: what the model is missing, and
    every relationship still pointing at it, with who needs it and how.
  - **Copy name reads the same everywhere**: the format first, then what to copy.
  - **Item menus are grouped by what each choice costs.**
  - **The Editor's tab carries the unsaved dot too**, so pending changes show even
    from the background.
  - **Discard says what it would throw away**, counted by part of the model. Every
    panel asks the same way.
  - **A multi-format logical file is marked the same way everywhere.**
  - **Implied foreign keys**
    - **A search and its findings are kept with the model** and travel with it. The
      list, the readings taken from the data and the candidates you turned down are
      all there next time. Nothing joins your items or diagrams until you accept it.
    - **Searching again, or checking the data again, asks first**, and says what it
      is about to replace.
    - **The Extractor and the Editor offer the same candidates**, found and judged
      the same way.
- **Object & Sources: an analysis opened from a file says how much it holds.**
- **Scan Server Sources: the note on how you are searching speaks only when it has
  advice**, which is that for the terms you have entered, the other way is likely
  to be quicker.
- **Native Query Info: the definition tab says a batch job is printing it**, and
  how long that takes. Open the tab again to retry.
- **Tools Settings: a switch is named after what it turns on**, and a field holding
  a list takes the full width.

### Fixed
- **Source types and members**
  - **Every source member is listed and counted, typed or not**, in Navigate
    Server, Object & Sources, Library Compile Order and the commands that open an
    object's source. A member with no type says so, and its group is on the summary
    to click.
  - **A member with no source type makes the round trip**: downloaded, listed,
    paired by Sync Local Project, and uploaded back as it was.
  - **Downloading a library keeps to its source files.**
- **Object & Sources**
  - **Every member of a name is listed and counted**, however many source files
    share it, each paired with the object of its own kind.
  - **A name with more than one counterpart pairs the same way every time.** An
    object is judged against its most recent source, a member against its oldest
    object, so a rebuild that is due is reported as due.
  - **A library's own source files are no longer counted as objects missing a
    source**, and say why, so the totals add up.
  - **A DDM file is no longer reported as an object whose source is missing**, and
    says why: it is created by a command, never built from a source member.
  - **An SQL procedure or function is paired with what it built.**
- **Data Model**
  - **A library is extracted and compared on its data files**, whole library or
    name pattern.
  - **Data Model Comparison: library against library offers the actions that fit
    it**, leaving out the model's own Save and Discard.
- **Dump**
  - **A field declared with only a length reads as the character field it is**,
    here and in the Data Model's extraction from native sources.
  - **Hide default values hides a packed zero and a date nobody set.**
- **Open Referenced Object Source, from local, looks where you are working**: the
  projects open in Navigate Local, left to right, and then the folder open in VS
  Code.

## [1.2.5] - 2026-09-05

### Added
- **Scan Server Sources: a second way to search.** **IBM i Native Search** has the
  server search its own source, several times faster over a large library, for one
  plain-text term. Picked from the gear beside the options or set as your default.
  - The panel offers only what the chosen way supports, so a search always runs as
    it reads on screen.
  - Where the server cannot offer it, the panel is set to **Unix Search** and waits
    for you.
  - It says when the other way would be faster, before the waiting starts.
- **Data Model Comparison**
  - **Four tabs.** Differences are split into **Items**, **Dependencies**,
    **Processes** and **Diagrams**, each listing what it is about the way the Data
    Model Editor lists it. The Items tab now shows one row per object rather than
    one per column.
  - **Processes and diagrams are compared**: added, removed, renamed, and covering
    a different set of objects. Between two model files, the only side that carries
    them.
  - **Apply a change.** The badge in the **To do** column makes the change it
    names. Everything applied stays unsaved until you save it in the Data Model
    Editor.
  - **Replace or merge.** A process or diagram both models have offers both:
    **replace** takes the other version, **merge** adds to what is already there.
  - **Open a row.** Double-click to see the object or dependency in the same views
    the Data Model Editor uses, marked up with every difference in it.
  - **Processes and Diagrams show two tables**: the list on the left, the objects
    the chosen one covers or draws on the right.
  - **Impact**: what a change reaches beyond the model, meaning programs that may
    need recompiling, glossary entries, and the diagrams and processes the object
    appears in.
- **File Viewer, RPG data structure.** Initialising from the first record uses the
  first record **as shown** in the Data tab, with its filters and its sort.
- **Tooltips everywhere.** Every button, box, tab and tick box explains what it
  does on hover, and every entry box shows an example or its default.
- **Procedure Change Impact Analysis**
  - **Confirm in source** reads the sources of the objects bound to the one holding
    the procedure and reports which of them name it. A miss reads **no explicit
    evidence** and never changes the rebuild action.
  - **Include callers (call chain)** optionally lists the programs that call an
    impacted program, counted separately as needing no rebuild.
  - **Save** and **Open** a rebuild plan, including any source confirmation already
    run.
- **Library Compile Order**: **Save** and **Open** a compile order, a right-click
  menu on each row (open or copy a source, copy names), and **Run action** on the
  members you select.
- **Programs Level Check Analyzer**: **Run action** on the programs selected in
  **Programs to Recompile**.
- **Object Change Impact Analysis**: the **Recompile Order** tab gains row
  selection and the same right-click menu as the results, including **Run action**
  on the steps you select.
- **Object Change Impact Analysis and Programs Level Check Analyzer**: a source
  that is no longer where the object records it is marked in orange, so a rebuild
  is planned around what is there. A chip says so when the check cannot run.
- **Review Authority Failures, All columns**: ask the journal for every column it
  can return, for when you need a field the panel does not list.
- **User Info**: the attribute sections collapse, and stay collapsed while you look
  up other users.
- **Programs Signatures Analyzer** is now listed in the Tools4i view, under Objects
  References, and marked beta there.
- **Data Model Extractor**: how native source is read is now a setting rather than
  a choice on the panel. Both routes give the same result and it falls back on its
  own if one fails.
- **Startup settings.** **Reopen panels on startup** brings back the Tools4i panels
  that were open when VS Code was closed, and **Open the Tools4i view on startup**
  opens the Activity Bar view. Both are off by default, so nothing opens on its own
  unless you ask for it.
  - A restored Navigate tab comes back as the one it was, **Server** or **Local**,
    with its own search criteria.
- **Data Model Editor, Health**: two coverage sub-tabs, **Items with no process**
  and **Items with no diagram**, listing what has not been documented yet. Neither
  counts towards the issue total.
- **Dump Files Viewer**
  - **Parse Data**: read a record buffer as the file's fields instead of as bytes.
    The result says where the layout came from, and marks what could not be read.
  - **File Viewer**: each file the program had open offers a button to browse it,
    in the library the dump names.
- **Navigate Server: a search that cannot be narrowed says so**, and says what
  would narrow it.

### Changed
- **Scan Server Sources**
  - **A search over many libraries starts much sooner.** Working out which members
    to look at is one question now, whatever the number of libraries.
  - **A wide scan looks only at the source files that hold members.**
  - **A very wide search returns what fits** and says the result is incomplete. How
    many lines it carries is a setting.
  - **A library pattern scans every library it matches**, wherever the wildcard
    sits in it.
  - **Fewer trips to the server**, so a wide scan finishes sooner.
- **Scan Local Sources**
  - **A large folder is searched three times faster**, and the hits list in the
    same order on Windows, Linux and macOS.
  - **A source's description is found whatever case its file is named in.**
- **Sources Scan Results**
  - **Opens in the same tab group as the other panels.**
  - **Save and Export** are on a search's right-click menu, acting on that search
    whichever one is showing.
  - **Library priority folds away** and scrolls in its own box, so a scan over many
    libraries still leaves the results in view.
  - **Load is now Open**, matching the other panels.
- **Navigate Server**
  - **Searching by name is much faster.** A name ending in a wildcard is looked up
    by the server. One starting with a wildcard still has to be searched for.
  - **Listing members is faster**, read from the catalogue in one question instead
    of asking each source file in turn.
  - **A wildcard on its own covers every library when listing objects**, the
    system's own included. Members and libraries keep to user libraries.
  - **Library**: a pattern behaves the same under all three targets.
  - **Type** accepts a pattern.
  - **Members with no source type are listed**, and open as plain text.
  - **Attribute** is offered only where it applies.
  - **Columns that could not say anything are gone**: Attribute when listing
    members, Type and Last used date when listing libraries.
  - **Cancelling a long search** stops the remaining libraries being asked about.
  - **The results table keeps up with a long result.** Only the rows on screen are
    drawn, and a quick filter redraws once you pause typing rather than once a
    letter.
  - **Downloading a library**: the download folder is asked for before the
    library's source members are listed, so you choose before any of the waiting.
- **Navigate Local**
  - **A large project lists in a fraction of the time.** The scan asks each file
    for its entry instead of opening and reading it, and only the rows on screen
    are drawn.
  - **Size replaces Lines**, read straight from the file.
  - **Cancelling a scan** stops it at once and says so.
- **The log**
  - **Says where a local search and a project listing spent their time.**
  - **Records what the server was asked to run.**
- **Tools4i Settings: a setting's choices are listed by name** where it gives them
  one.
- **Sources are downloaded with upper-case names**, as the IBM i holds them,
  whichever route downloads them, so a source and its description always find each
  other.
- **Data Model Comparison**
  - **Differences read as work to do.** Each row says what to do in your model, not
    what the two sides look like: **add**, **remove**, **update**. The saved model
    is always the side being brought up to date, whichever mode you compare in.
  - **Re-read the server** is offered only where it does something, which is
    comparing against the server. Library against library always reads afresh.
  - The filters, the exports and the table appear once there is a result to filter.
  - A comparison of two whole libraries keeps up: only the rows on screen are
    drawn, and typing in the search box redraws once you pause rather than once a
    letter.
  - Relationships drawn or confirmed by hand are kept when the other side is read
    from the server, which cannot carry them. The summary says how many were
    skipped.
- **Data Model Dictionary**
  - The three review actions are behind one **Actions** menu and the two export
    buttons behind one **Export**, leaving the search box room to be usable.
  - The table keeps up on a large model: the context menu opens at once and quick
    filters keep pace as you type. The Description column shows its full text on
    hover and in the edit box.
- **Job Info, Call Stack**
  - The library and program of each frame stand out, so the programs read down the
    stack at a glance. A **Hide system frames** tick box leaves only your own
    programs, and the frame numbers keep their real position in the stack.
  - A program's source is looked up in the object's own library first, then the
    library list, and only then the library recorded when the object was compiled.
- **Every Data Model panel now works on the same unsaved copy**: the Extractor,
  Editor, Viewer, Dictionary and Comparison. A change made in one is visible in all
  of them straight away, and **Save changes** or **Discard** from any of them
  commits or drops the lot.
- **Item and relationship views**: **Check on server** is a secondary button in
  both, as an aside rather than the reason the dialog was opened.
- **IBM i names are typed in upper case.** Library, object, member, source-file,
  user and procedure boxes fold what you type, as the server stores it.
- **Objects References**: the beta mark moves from the whole group to the
  individual tools still in beta.
- **Column headings** keep initialisms in capitals: PTF, IPL, ID, ASP and the rest.
- **Right-click menus act on the selection**, not on the row under the pointer.
  Entries that can only do one thing at a time, such as opening a source or a
  panel, appear only when one row is selected, and the ones that work on many say
  how many.
- **Review Authority Failures**: while a long read is running the panel shows what
  it is reading and for how long, and says that the range, not **Max rows**, is
  what makes it slow.
- **User Info**: the filter sits above the attributes it filters, and only the
  attributes scroll. The user, the related links and the filter stay in view.
- **PTF Status, Review Authority Failures and Journal Viewer**: the results filter
  appears once there are results to filter.
- **Data Model Editor, Health**: **Orphan items** reports connectivity only,
  meaning items no relationship or dependency touches.
- **Navigate Local and Upload Local Project**: uploading proposes the library the
  project folder is associated with, and picking a folder fills the Library field
  with it.
- **Dump Files Viewer and Job Info, Call Stack**: a source opened from either lands
  on the statement the frame records, and says so when that statement is not a line
  of the member.

### Fixed
- **Scan Server Sources: Cancel gives the panel back at once**, however wide the
  search.
- **Downloading a library**: **Open in Navigate Local** opens on the library just
  downloaded.
- **Upload Local Project**: a source-file folder named in lower case uploads
  against the right source file on the server.
- **Data Model Comparison**
  - **Saved model against another model file**: differences read as changes to make
    in your model, the same way as every other mode.
  - **Re-read the server**: the tick box appears where it applies, and hiding it
    works.
  - The library boxes suggest generic example names.
  - An object is compared only on what both models recorded, and the summary says
    how many were compared in part.
- **Data Model Viewer**: a diagram opened from the model, and the list of diagrams
  to choose from, both show the changes still waiting to be saved.
- **Data Model Viewer and Data Model Dictionary**: edits made in either survive a
  save in the Data Model Editor, because all three work on the same unsaved copy.
- **Object Change Impact Analysis**: files built from DDS show their source, so
  **Open Source** and **View data** are offered for them and their sources copy
  along with the programs.
- **Object Change Impact Analysis and Programs Level Check Analyzer**: a source is
  looked for in the object's own library and the library list before the library
  recorded when it was built, so a promoted object opens the copy that exists.
- **Programs Signatures Analyzer**: every signature in the list is read exactly as
  the object holds it.
- **Review Authority Failures**: a **To** date earlier than **From** is reported as
  such, and failures appear in the panel as well as in a notification.
- **Data Model panels**: tooltips keep to what each action does.
- **Navigate Server**: **Add Library to LibL** adds the library, and it stays in
  the library list.
- **Data Model Editor, Health**
  - The tables keep up while you type in a column filter.
  - Selecting a row keeps your place in a long list.
- **Source member dates**: **Last modified** and **Created** show the time the IBM
  i recorded, in its own time zone.
- **Sync Local Project and Run Action on Server**: that same time decides whether a
  member is **newer on the server** than the local copy, and dates a downloaded
  source.
- **Dump Files Viewer, Open source**: asks the program where its source is, and
  opens it straight away.

## [1.2.2] - 2026-08-25

### Added
- **Tools4i view**: tools can be marked as **favourites**. Hover a tool (or focus
  it with the keyboard) and click the star, and it appears in a **Favorites**
  section at the top of the tree, sorted by name. The tool stays listed under its
  own category too, starred there as well, so it never disappears from where you
  are used to finding it, and the star can be cleared from either place. Favourites
  are remembered per user and travel with Settings Sync.

### Fixed
- **Tools4i view**: the sidebar no longer opens itself every time VS Code starts.
  Reopening the category that held the last tool used was dragging the whole
  sidebar into view with it, whether or not it had been open when the window was
  closed. The category now reopens without touching the sidebar.
- **All panels**: a Tools4i panel no longer reappears, empty, when VS Code starts.
  Every panel is a live view over a server connection, so a tab restored from a
  previous session, sometimes one well in the past, could only come back blank. A
  restore is now accepted and the panel closed, leaving the workspace as it was.
- **Message File Editor**: opening a large message file no longer freezes the
  window. A file with tens of thousands of messages was drawn in full, in one go.
  The table now draws at most 500 rows at a time and says how many matched, so the
  search box and the column filters are used to reach the rest. Every message stays
  loaded, so saving and the duplicate-ID check still see the whole file. Sorting a
  column on a file that size also went from roughly three seconds per click to
  under a fifth of a second, with the same ordering as before.
- **Message File Editor**: loading a message file can be **cancelled**. It could
  previously sit on "Loading" indefinitely with no way out if the server did not
  answer.
- **Quick filters**: switching them off now stops them narrowing the table in the
  panels that were still applying them, which were **Message File Editor**,
  **Binding Directory Editor**, **Binding Directory Sync**, **Jobs**, **Routines**
  and **Spooled Files**. The filter text was still in effect even though the filter
  row was hidden, so rows stayed filtered out with no visible reason. The text is
  still remembered and comes back when the filters are switched on again. In the
  Binding Directory Editor this also restores drag-reordering, which an invisible
  filter was blocking.
- **Diagnostics**: a server call that never returns is now reported. Until now a
  call was only written to the log once it came back, so a request that hung left
  no trace at all, and the log looked idle precisely when something was stuck.
  Anything still outstanding after five seconds is now logged, and a follow-up line
  records it if it later returns.

### Changed
- **Navigate Server and Navigate Local**: pressing **Find** now shows a progress
  notification naming what is being searched, and the button reads **Searching**
  and is held down until the result comes back. The panel keeps showing the
  previous result while a search runs, so there was nothing to say the click had
  landed and the natural reaction was to press again and queue another round trip.
  The Navigate Server search is also **cancellable** now, which matters for a
  search across every user library.

## [1.2.0] - 2026-08-24

### Added
- **Scan Server Sources and Scan Local Sources**: search terms are now built one at
  a time with an **Add** button and listed as removable chips, instead of a growing
  stack of condition rows. The match operators read as **Matches** and **Does NOT
  match**, and the Options are grouped under captions so combining, matching and
  column range read as three separate decisions.
- **Sources Scan Results**: right-click a result tab for **Load in Scan Sources**,
  which reopens the exact criteria that produced it in Scan Server or Scan Local
  Sources according to where it came from, and **Copy Search Parameters**.
- **Navigate Local, Run Action on Server**: run one of your own Code for IBM i
  Actions against a local source, compiling into the IBM i library the project
  folder is associated with. How the source gets onto the server is a setting: it
  can be uploaded to the matching source file and left there, or staged into a
  scratch source file sized to fit and cleared afterwards. Both run under the
  current session's library list, and neither changes your current library. Also
  available as **Tools4i: Run Action on Local Source** in the command palette.
- **Navigate Local**: compile errors are read from the compiler's own event listing
  and shown in the **Problems** panel against the local file, including errors
  raised inside `/COPY` members, which are prefixed with the copybook name. The
  Action has to specify `OPTION(*EVENTF)`.

### Fixed
- **Navigate Local**: switching **Quick filters** off now stops them narrowing the
  table. Their text was still being applied even though the filter row was hidden,
  so rows stayed filtered out with no visible reason. The filter text is still
  remembered and comes back when they are switched on again.

### Changed
- **Navigate Local**: columns can be **resized** by dragging the header dividers,
  and double-clicking a divider sizes that column to its widest visible value, the
  same as in **Navigate Server**. Description keeps absorbing the leftover width.
- **Navigate Local**: the status bar now shows a one-line **summary of the
  criteria** behind the current result, which matters most once the filter bar is
  folded away.
- **Navigate Server and Navigate Local**: the **Del** key now deletes the selected
  rows, with the same confirmation as the context menu. Both menus already
  advertised the shortcut but nothing was listening for it.
- **Navigate Local**: rows can now be **selected**, with Ctrl or Cmd click to
  toggle and Shift click for a range, the same as in **Navigate Server**. Editing
  the Name, Type or Description in place now needs the row to be the only one
  selected, so a first click selects instead of opening an editor. Right-clicking
  several selected rows offers a batch menu: **Open**, **Copy Name**, **Upload to
  Server** (asking for the target library once) and **Delete** (one confirmation
  for all).
- **Navigate Local**: **Upload to Server** now creates the target source physical
  file when it is missing, sized and encoded as the project recorded it, instead of
  failing. Uploading a source whose type and description have not changed no longer
  costs two extra server commands.
- **Navigate Server**: the **Attribute** column now shows the PDM-style attribute
  for physical files, `PF-SRC` or `PF-DTA`, instead of the bare `PF`. Filtering by
  either the full or the bare attribute still works.

## [1.1.0] - 2026-08-21

### Added
- **File Viewer, Custom fields**: **Open** and **Save** buttons to save a
  field-definition set to a file and load it again later.
- **Source Search**: a **Copy to Library** bulk action for selected members,
  replacing **Copy member**.
- **Data Model**: items now have an editable **Note** field, editable from the
  item's edit form, shown read-only in the Viewer, listed in the Data Model
  Dictionary's "Used by" table, and included in both the Dictionary's and a
  diagram's generated documentation. The Editor's Items table shows a small icon on
  items that have one.
- **Data Model Viewer and Editor**: a shared **Add Items** dialog (single item,
  library and name wildcard search, from a process, or from a saved diagram or
  file) for adding items to a diagram or assigning them to a process. The Editor's
  Processes tab gained an **Add item to process** action that opens it.
- **Data Model Viewer, Show Item Note**: pin an item's Note onto the diagram as a
  read-only note linked to it with a connector line, kept in sync with the item's
  actual Note. An **Add to canvas** shortcut appears next to the Note in the item
  info panel while it isn't shown yet.
- **File Viewer, Custom fields**: **Import from RPG input specs** now also reads
  data structures whose subfields are positioned by overlay rather than by explicit
  From and To columns, and free-format source, in addition to fixed-format specs.

### Changed
- **File Viewer** (from the editor's right-click menu) now resolves the file name
  highlighted in the source and opens that file, instead of always opening the file
  the current member itself belongs to. It still falls back to the current member
  for DDS and SQL sources when nothing is selected.
- **Open Referenced Object** confirms the resolved target after opening it, and
  validates a highlighted local-source name the same way as the IBM i lookup.
- **File Viewer, Custom fields tab**: Refresh, Export and Max rows moved next to
  the retrieved-data grid.

### Fixed
- **Source Search**: source files are now recognised from the database catalog
  rather than guessed from the object's attribute name, so a source file whose
  attribute does not happen to say so is still found.
- **Data Model Extractor**: a view built on another view is now classified as a
  view over a view, instead of a view over a table.
- **Data Model Extractor**: column protection no longer flags every column. It now
  reads the catalog's own record of which columns actually carry a field procedure,
  instead of a flag that answered for all of them.
- **Data Model Editor**: no longer re-opens the last-edited item's dialog on later,
  unrelated actions.
- **Data Model Editor**: "Processes (n)" in the item edit form now shows how many
  processes the item is actually assigned to, instead of the model's total process
  count.
- **File Viewer, Custom fields**: **Import from RPG input specs** is now much more
  robust against real-world source: change-level markers in the sequence-number
  columns, listing line-number prefixes copied from a source browser, length and
  type written with no space between them, comment lines where the marker is glued
  to the asterisk, array subfields (now sized for the whole array instead of one
  element), subfields with no explicit decimals (now defaulting to none instead of
  blank), and a rare case where a fixed-format calculation line was misread as a
  free-format declaration.

## [1.0.0] - 2026-08-18

First public release. Everything below runs from the **Tools4i** view in the
Activity Bar or from the Command Palette, and works against the server.

### Browse and search
- **Navigate Server and Navigate Local**: browse libraries, objects and source
  members with filters by name, type, attribute, description and date. Maintain
  descriptions and source types, rename, copy and delete, and download sources to a
  local project, whether one member, a source file or a whole library.
- **Scan Server Sources and Scan Local Sources**: content search across several
  libraries at once, with target and omit lists and a column range.
- **Sources Scan Results**: results per scan with library priority, per-column
  filters, export, and the option to hide matches that fall on commented-out code.
- **Open Referenced Object Source**: from a name selected in the editor, open its
  source resolved in library-list order, or from the open project.

### Compare, sync and transfer
- **Sync Local Project** and **Sync Server Library**: member-by-member comparison
  and sync in either direction.
- **Upload Local Project**: upload with a preview of what will be created and
  replaced, character-set control, and `*BNDDIR` creation from the binding
  directories the project carries.
- **SavF Manager**: inspect save files and restore everything, a library, a set of
  objects or a single object into the library you choose.

### Editors
- **Binding Directory Editor and Sync**: the whole entry list at once, comparison
  against another binding directory, and a check that every referenced object still
  exists.
- **Message File Editor**: view, add and edit the message descriptions of a
  `*MSGF`.

### Operate
- **Spooled Files Manager** and **Dump Files Viewer**.
- **Jobs Manager**, **Job Info** across ten tabs, **Job Log Viewer**, **Job
  Description Info** and **Message Queue Viewer**, including replying to inquiry
  messages.

### Database
- **File Viewer**: data filtered by a condition and editable, field definitions
  with record positions, dependents, generated RPG data structures, and custom
  fields for program-described files.
- **Journal Entries Viewer**, **Stored Procedures Manager**, **Native Query Info**
  and **Data Area Info**.

### Data model
- **Data Model Extractor**: from the Db2 catalog, from native DDS and SQL sources,
  or from a DDL script.
- **Data Model Editor** and **Data Model Viewer**, with entity-relationship
  diagrams that include logical and multi-format logical files, plus **Data Model
  Dictionary**, personal-data classification with mandatory human review, model
  health checks and **Data Model Comparison**.
- Implied foreign keys: candidates rated by confidence and verified against the
  catalog or against the data itself.

### Object references and impact (beta)
- **Programs Level Check Analyzer**, **Native Query Level Check Analyzer**,
  **Object Change Impact Analysis**, **Procedure Change Impact Analysis**,
  **Library Compile Order** and **Object & Sources**. This group is in beta testing
  and is marked as such in the side bar.

### System, users and safety
- **PTF Status**, **User Info** and **Review Authority Failures**.
- **Protected libraries** and **production protection**, blocking destructive
  changes, uploads, sync writes and editor saves against systems that are not
  development systems.

### Settings and about
- **Tools4i Settings**: every setting the extension contributes in one searchable
  form.
- **About Tools4i**: version, author, licence and the Code for IBM i build in use.
- Site-defined column-name patterns for the personal-data scan, kept in your own
  settings.
