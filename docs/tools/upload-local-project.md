---
title: Upload Local Project
layout: default
parent: Transfer
nav_order: 1
permalink: /tools/upload-local-project/
---

# Upload Local Project
{: .no_toc }

A whole project back to a library in one operation, with the questions that usually
get answered too late asked up front.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Upload Local Project**.

| Field | What it takes |
|---|---|
| **Folder** | The project base folder. Its metadata subtree supplies each source's library, file, member and type, with the character set and record length |
| **Library** | The server library to upload into |
| **Source file**, **Member**, **Type** | Narrow the upload. All three take wildcards and default to everything |

## Preview first

**Preview** lists what **would** be uploaded without changing anything on the server.

It is worth the extra click every time: it is where a mistyped library name shows up
as four hundred creations instead of twelve replacements.

## When a member is already there

| Choice | What happens |
|---|---|
| **Replace** | The member is overwritten |
| **Skip** | It is left alone |
| **Prompt** | You are asked, member by member |

## When the source file is not there

**Create missing source files** does that, and the **default character set** beside it
is used when the project's metadata does not record one. The default, 37, is US
EBCDIC.

A source file created with the wrong character set is a problem discovered weeks
later, by somebody else, in a compile listing. This is the moment to get it right.

## When a character cannot be written

A character in your source with no equivalent on the server has to become something.
You decide which:

- **Replace it**, with the character in the box beside the option (a space by
  default),
- or **skip the member**, leaving it untouched on the server.

Deciding here beats finding out afterwards, one byte at a time.

## What else travels

Three tick boxes:

- **Descriptions**, so a member keeps its text,
- **Dates**, so the change dates are carried,
- **Binding directories**, which creates or replaces `*BNDDIR` objects from the
  `.BINDIR` files in the project.

## Members on the server that are not in the project

The result lists them separately, because they are the other half of the question:
they exist in the library and not in your folder. Both result lists have a **quick
filters** switch of their own, which matters on an upload of several hundred members.

**Delete all listed** removes every one of them from the server. It cannot be undone
from here, which is why it is a button of its own and not part of the upload.

## Related

- [Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/), for going member
  by member instead.
- [Binding Directory Editor]({{ site.baseurl }}/tools/binding-directory-editor/)
