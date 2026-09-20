# Security and privacy

What Tools4i does, and does not do, on the machine you install it on.

This page is written for the person who has to approve the extension as much as
for the person who uses it. If your organisation needs something stated here that
is missing, ask and it will be added.

## The short version

- **No network connections of its own.** Nothing in the published package fetches
  a URL, opens a socket or calls home.
- **No telemetry, no analytics, no account, no licence check.** Nothing is
  counted, nothing is reported, and there is nothing to sign in to.
- **One system, and it is yours.** The only machine Tools4i talks to is your own
  IBM i, over the connection Code for IBM i already holds.
- **No server component.** Nothing is installed on your IBM i. One optional
  feature, switched off until you turn it on, asks before it compiles a 55 line
  CL program on your system, and
  [its source is published here](server/IUDUPSP3.clle). A setting switches that
  feature to a mode that compiles nothing, or turns it off altogether, and on
  production the deploy is blocked by default.
- **MIT licensed**, with the licence travelling inside the package.

## Network

Tools4i makes no network calls of its own. The published package contains no HTTP
or socket client of any kind: no browser fetch, no request object, no web socket,
and no use of the platform's network modules.

That also means there is no update check, no configuration downloaded at startup,
no crash reporter and no remote feature switch. When Tools4i is idle, it is idle.

Extension updates come from your editor's marketplace, the same way every other
extension is updated, and not from the extension itself.

## Your IBM i connection

Tools4i does not open a connection to your server. It works through the one
**Code for IBM i** has already established, and everything it reads or writes on
the server travels over that connection.

Because of this, Tools4i bundles no connection client at all: no SSH client, no
database driver, no Java toolkit. There is no second door into your system to
review, and no place in Tools4i where server credentials are entered or kept.

What it does on the server is what you asked for from a panel, done as the user
your connection is signed in as, and bounded by that user's authority. Nothing
runs on a schedule and nothing runs in the background without a panel of yours
having asked for it.

## What Tools4i puts on your IBM i

Tools4i has no backend. It installs no library of objects, no server component,
no exit program and nothing that runs while you are away. What it does on the
server, it does through your Code for IBM i connection with standard commands and
catalogs.

There is one exception, and rather than ask you to take it on trust, here it is
in full.

**Duplicating a spooled file.** In `program` mode, the first time you duplicate
a spooled file, Tools4i asks whether to create the program, naming it and the
library it would go in. Only if you agree, it creates a `QCLSRC` source file in
the library you configured, uploads a 55 line CL program into it, and compiles it
with `CRTBNDCL`. From then on it is called, not rebuilt. The program calls eight
public IBM APIs to read one spooled file and write another, runs in your own job
as your own user, and needs no authority that user does not already have.

**It is optional, and it is a setting.** Nothing is compiled unless three things
are true at once: you have set **Duplicate mode** (`tools4i.dupSpoolMode`) to
`program`, you duplicate a spooled file, and you say yes when asked. The setting
arrives at `off`, and until it is changed the copy options do nothing but point
back at it. It is yours to change at any time, in **Tools4i Settings** or in your
own settings file. Set to `command`, the same button calls a duplicate command
already installed on your system and compiles nothing at all. Which library the
deploy would use is a setting too, and so is whether deploys are allowed on this
system.

**The source is in this repository:** [`server/IUDUPSP3.clle`](server/IUDUPSP3.clle).
It is the text that gets compiled, character for character, and
[`server/README.md`](server/README.md) says when it is compiled, where it lands,
what each API call is for, and what stays behind. What stays is the program and
the source member it was built from, so anybody on your system can read what is
running there and compare it with the file published here.

**Where it lands is the temporary library your connection already uses.** Out of
the box, **Deploy library** (`tools4i.dupSpoolDeployLibrary`) is `ILEDITOR`, which
is the library Code for IBM i creates for its own temporary objects. Left blank,
the setting follows whatever temporary library your connection is configured
with, under whatever name you gave it. Either way, unless you deliberately name a
library of your own, the program is built in the connection's temporary library
and never in an application or production library.

**Any one of these means it never happens:**

- **Leave Duplicate mode (`tools4i.dupSpoolMode`) at `off`**, which is how it
  arrives. The copy options do nothing but point back at the setting, so nothing
  can start a deploy.
- **Do not use the feature.** Nothing else triggers the deploy.
- **Set Duplicate mode (`tools4i.dupSpoolMode`) to `command`**, and Tools4i calls
  a duplicate command already installed on your system instead, by default
  `TAATOOL/DUPSPLF`. Nothing is uploaded and nothing is compiled.
- **Name the library in Protected libraries (`tools4i.protectedLibraries`)**,
  which takes names and wildcards such as `PROD*` or `*TEST`. Tools4i refuses to
  write to anything that matches.
- **Leave production protection alone.** **Block editor saves and deploys on
  production** (`tools4i.production.blockEditorSavesDeploys`) is on by default and
  blocks this deploy on every system you have not registered as a development
  system. On production, nothing is deployed unless somebody turns that off on
  purpose.

## Your data

Your source, your data and your job output stay between your machine and your IBM
i. Nothing is uploaded anywhere else, because there is nowhere else to upload it
to.

What Tools4i writes on your machine is what you ask it to write:

- **Settings**, in your own VS Code settings, like any other extension.
- **A few small preferences your editor keeps for any extension**: which tools you
  starred as favourites, and which panels were open last time if you asked for
  them to be reopened.
- **Files you save from a panel**: downloaded sources, exported CSV files,
  snapshots of a job log, a job, a message queue or an analysis, data model files,
  diagram images, and spooled files you download.

Each file is written where you choose, when you press the button that writes it.

The diagnostics log, when you switch it on, is shown in your editor's Output
panel and is not written to disk.

## Running other programs on your machine

Tools4i launches an external program in exactly two places, and both are visible
from the panel that does it:

1. **Opening a downloaded spooled file** with the viewer your operating system
   associates with that file. The file has already been downloaded to the location
   you chose, and this is the same action as double-clicking it.
2. **Converting a printer file to PDF** with GhostPCL, which is a separate,
   third-party tool that you install yourself and point at from the settings. It
   is run from the path you configured, with a fixed set of arguments, and without
   going through a shell.

If you never configure a PDF tool, the second one never runs. No other program is
started on your machine, and what runs on the server is covered above, in
[What Tools4i puts on your IBM i](#what-tools4i-puts-on-your-ibm-i).

## What is in the package

Three declared dependencies, all of them for drawing graphs, and five packages in
total once their own dependencies are counted:

| Package | What it is for |
|---|---|
| cytoscape | Draws the data model diagrams |
| cytoscape-dagre | Connects the other two |
| dagre | Lays the diagrams out |

Every bundled component and its licence is listed in
[THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md), which also travels inside the
package.

The CL program described above travels in the package as well, as text, which is
how it reaches your system when you ask for it.

Tools4i itself is MIT licensed, and the licence file is included in the published
package.

## Package integrity

The package published on the Visual Studio Marketplace is signed, and VS Code
verifies that signature when it installs or updates the extension. If the file has
been altered, the editor refuses it.

There are two places the author publishes Tools4i, and only two: the
[Marketplace](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i)
and [Open VSX](https://open-vsx.org/extension/tools4i/tools4i). This repository
holds documentation, never a build. A packaged file offered anywhere else did not
come from the author, and the signed Marketplace build is the one to prefer where
you can use it.

## Protections you can switch on

Tools4i writes to the server, so it ships with two guards against writing to the
wrong one. Both cover the spooled-file deploy described above, and the second one
blocks it on production without you doing anything:

- **Protected libraries**: libraries the extension must never modify. Copy,
  rename, delete, change-text, deploys, sync writes and editor saves are all
  blocked there, and source members from them open read-only.
- **Production protection**: any connection whose host name or IP address is not
  in your list of development systems is treated as production. Destructive
  changes, object creation, uploads, sync writes, editor saves and deploys can
  each be blocked, and the interface carries a red production warning so nobody
  works on the wrong system by accident.

Both are configured in **Tools4i Settings**.

## Reporting a security problem

Please report anything security related **privately**, by email, rather than in a
public issue:

**tools4i.support@gmail.com**

Tell me what you found, how to reproduce it, and the version you saw it in. You
will get an acknowledgement, and a fix will be published as a new version with the
problem described in the changelog once it is available to install.

## Supported versions

The current published version is the supported one. Security fixes are shipped as
a new release rather than backported, so the fastest route to a fix is to keep the
extension updated.
