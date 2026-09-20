# The only code Tools4i compiles on your IBM i

Tools4i has no backend. It installs no library of objects, no server component,
no exit program and no daemon. It works through the connection Code for IBM i
already holds, using standard commands and catalogs.

There is exactly one exception, and it is in this folder:
[`IUDUPSP3.clle`](IUDUPSP3.clle), a 55 line CL program. It belongs to one optional
feature that arrives switched off, so this program only ever exists on a system
where somebody turned that feature on, duplicated a spooled file, and agreed,
when asked, to it being created.

This page says when it is compiled, where, what it does, what it leaves behind,
and how to make sure it never happens at all.

The source here is the source that gets compiled. Not a summary of it, not an
extract: the same text, character for character.

## What it is for

Duplicating a spooled file, from the Spooled Files Manager.

**Duplicate mode** (`tools4i.dupSpoolMode`) decides how, and it has three values:

- **`off`**, which is what it ships as. The copy options in the Spooled Files
  Manager do nothing but point back at this setting, so there is nothing to
  trigger and nothing to compile.
- **`command`** calls a command that already exists on your system, by default
  `TAATOOL/DUPSPLF` from TAA Tools. Nothing is deployed, nothing is compiled.
- **`program`** uses this CL program, compiling it on your system the first time
  you duplicate a spooled file, and only after asking you.

The program exists because it is compiled on the system it runs on, so it reads
the spooled-file attribute layout that system actually uses. That is why it works
where a back-level copy of a duplicate command fails partway through.

## When and where it is compiled

The first time you duplicate a spooled file in `program` mode, and only then:

1. Tools4i checks whether the program is already there. If it is, nothing else
   happens, now or ever again.
2. If it is not, you are asked first. The question names the program and the
   library it would go in, and says what else goes with it. Decline and nothing
   is created and nothing is duplicated.
3. A `QCLSRC` source file is created in the target library if it is missing, a
   member is added, and the source in this folder is uploaded into it.
4. The program is built from that member with `CRTBNDCL`.

The target library is **Deploy library** (`tools4i.dupSpoolDeployLibrary`), and it
is the temporary library your connection already works in. Out of the box the
setting holds `ILEDITOR`, the library Code for IBM i creates for its own temporary
objects. Left blank, it follows whatever temporary library your connection is
configured with, under whatever name you gave it. Point it at a library of your
own only if you want the program somewhere else; nothing puts it in an
application or production library on its own.

All of it runs in your own job, as the user your connection signed in as, and
needs no more authority than that user already has.

## What it does while it runs

It calls eight public IBM APIs, all of them documented by IBM:

| API | What it does here |
|---|---|
| `QSPOPNSP` | Opens the spooled file you picked |
| `QUSRSPLA` | Reads that spooled file's attributes |
| `QUSCRTUS` | Creates a work space in `QTEMP` |
| `QUSCUSAT` | Sets that work space to extend as needed |
| `QSPGETSP` | Reads the spooled file's data into the work space |
| `QSPCRTSP` | Creates the new spooled file, in the output queue you chose |
| `QSPPUTSP` | Writes the data into the new spooled file |
| `QSPCLOSP` | Closes both spooled files |

It reads one spooled file and writes another. It does not read your database, it
does not touch objects other than the ones above, and it sends any failure back
as an escape message rather than swallowing it.

## What is left on your system afterwards

Two things, in the deploy library, both of which you can read yourself:

- The program object, `IUDUPSP3`.
- The source member it was built from, in `QCLSRC`. It is left there on purpose,
  so anyone on your system can read the source of what is running without taking
  anybody's word for it, and compare it against the file in this folder.

The work space is created in `QTEMP`, so it goes away with the job.

Nothing else is created, and the program is compiled once. Later duplicates just
call it.

## How to make sure it never happens

Doing nothing is already enough: **Duplicate mode** ships as `off`, and while it
is there the copy options do nothing but point back at the setting, so no deploy
can be triggered by anything. What follows is for a system where somebody turned
it on.

Any one of these is enough:

1. **Put Duplicate mode (`tools4i.dupSpoolMode`) back to `off`.** The copy
   options go back to pointing at the setting and doing nothing else. Set it to
   `command` instead and the copying stays, done by a command already on your
   system, with nothing deployed.
2. **Say no when it asks.** The first duplicate in `program` mode stops and names
   what it would create. Declining creates nothing.
3. **Never duplicate a spooled file.** No deploy is triggered by anything else.
4. **List the library in Protected libraries (`tools4i.protectedLibraries`).**
   Names and wildcards both work, so `PROD*` or `*TEST` covers a family of them
   in one entry. Tools4i refuses to write to anything that matches.
5. **Leave production protection on.** **Block editor saves and deploys on
   production** (`tools4i.production.blockEditorSavesDeploys`) is **on by
   default**, and it blocks this deploy on any system you have not registered as
   a development system. In other words, on production nothing is deployed unless
   somebody deliberately turns the protection off.

Every setting named here is in **Tools4i Settings**, and the last two are
described in [SECURITY.md](../SECURITY.md).
