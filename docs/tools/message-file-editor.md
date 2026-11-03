---
title: Message File Editor
layout: default
parent: Message files
nav_order: 1
permalink: /tools/message-file-editor/
---

# Message File Editor
{: .no_toc }

A `*MSGF` with its message descriptions on screen, searchable by identifier, by text
and by help.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Message File Editor**, with the library and
the name.

| Button | What it does |
|---|---|
| **Get Info** | Reads the messages from the server |
| **Open** | Opens a message file saved earlier and works on it with no connection |
| **Download** | Saves the whole message file, with its description, as a snapshot you can reopen offline |
| **Navigate to object** | Opens the `*MSGF` in [Navigate Server]({{ site.baseurl }}/tools/navigate-server/) |

As with the binding directory editor, **Save** applies to **the server** when the list
came from Get Info, and to **the snapshot** when it came from Open.

**Read-only** and **edit** are a choice you make at the top, so a message file opened
to look something up cannot be changed by accident.

## The table

| Column | |
|---|---|
| **State** | New, changed or removed, for edits not yet applied |
| **Message ID** | |
| **Sev** | The severity |
| **First-level text** | What the user sees |
| **Second-level (help)** | The Cause and Recovery text |
| **Format** | The substitution variables the message takes |

Every column filters. The **search** box above looks in the identifier, the first-level
text **and the help**, which is the one that matters: users quote the second line, not
the identifier.

## Editing

**Add message** creates a description. Rows are edited in place, and the help text
opens in a window of its own, where **OK** keeps it in the editor and **Cancel**
drops the change.

Nothing reaches the server until **Save**, and **Discard** reverts everything to the
loaded state.

## The format codes stay visible here, on purpose

Second-level help carries the system's own layout instructions in it, the ones that
force a new line or start an indented paragraph.

Everywhere else in Tools4i those are honored and turned into the layout they describe.
**Here they are left exactly as stored**, because here they are the text you are
editing. Hiding them would mean editing something other than what the system holds.

## Related

- [Message Queue Viewer]({{ site.baseurl }}/tools/message-queue-viewer/), which shows
  the same help the other way round, laid out as the system lays it out.
- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
