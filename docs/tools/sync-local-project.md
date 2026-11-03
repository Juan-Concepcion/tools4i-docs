---
title: Sync Local Project
layout: default
parent: Compare and sync
nav_order: 1
permalink: /tools/sync-local-project/
---

# Sync Local Project
{: .no_toc }

A folder on this machine and a library on the server, member by member: what is in
sync, what differs, and what exists on only one side.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Sync Local Project**.

| Field | What it takes |
|---|---|
| **Local** | The project folder. Its metadata subtree supplies the library, file and member mapping |
| **Library** | The server library to compare against |
| **File** | The source files to compare, `Q*` by default. Wildcards allowed |
| **Member** | The members, `*` by default. Wildcards allowed |

**Compare** reads both sides and matches them up. **Nothing is copied**: the result
only tells you what differs.

## Reading the result

Every member lands in one of four states:

| State | What it means |
|---|---|
| **In sync** | The same on both sides |
| **Different** | The content does not match |
| **Local only** | In the folder, not in the library. Usually your new work |
| **Server only** | In the library, not in the folder. Usually somebody else's |

**Only differences** hides the members that are in sync, which is almost always what
you want after the first look. The **filter** box narrows by name, with wildcards.

## Acting on a row

| Entry | What it does |
|---|---|
| **View** | Opens the member read-only |
| **Compare (Diff)** | The two sides side by side |
| **Edit local to Server** | Opens the local file with the server member beside it |
| **Edit Server to local** | The other way round |
| **Edit Both Sources** | Both open, editable |
| **Open local**, **Open Server member** | One side alone |
| **Upload (replace)** | Sends the local copy over the server member |
| **Download (replace)** | Brings the server copy over the local file |
| **Upload (create on Server)** | For a member that is only local |
| **Download (create local)** | For a member that is only on the server |

The create and replace entries are separate on purpose: the one you are offered says
what will happen, so a member that does not exist yet is never silently created by a
button labeled "replace".

## Bringing a lot down at once

**Download All** fetches the whole set in one pass, and it is several times faster
than it used to be. A member it cannot bring that way is still fetched on its own
rather than dropped, and anything that could not be brought at all is named.

## When you want the whole thing at once

[Upload Local Project]({{ site.baseurl }}/tools/upload-local-project/) pushes the
whole project in one operation, with its own preview of what will be created and what
replaced.

## Related

- [Navigate Local]({{ site.baseurl }}/tools/navigate-local/)
- [Sync Server Library]({{ site.baseurl }}/tools/sync-server-library/)
- [Upload Local Project]({{ site.baseurl }}/tools/upload-local-project/)
