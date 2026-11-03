---
title: Scan Local Sources
layout: default
parent: Search
nav_order: 2
permalink: /tools/scan-local-sources/
---

# Scan Local Sources
{: .no_toc }

The same search, over a project folder on this machine. Nothing is read from the
server.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Scan Local Sources**.

## The root folder

**Browse...** picks the project root, the folder that holds the `QRPGLESRC`,
`QCLLESRC` and other subfolders. It is given once for the whole scan, not per target.

## The search terms

Identical to the server side: type the text, press **Add**, and the term joins the
list as a chip that is either **Matches** or **Does NOT match**.

| Mode | What it means |
|---|---|
| **All terms** | Every term appears somewhere in the file, on any line |
| **Same line** | Every term appears together on one line |
| **Any term** | One term is enough |

With **Case sensitive** and **Regular expressions** beside them, and the same
**column range** for fixed-format sources, defaulting to 1 through 100.

## Targets and omissions

Built as a list, like the server side, but in the shape a folder has:

| Field | Meaning |
|---|---|
| Subfolder | Under the root, such as `QRPGLESRC`. Wildcards allowed |
| File | The name without the extension. Wildcards allowed |
| Type | The extension: `RPGLE`, `CLLE`, `SQLRPGLE`. Wildcards allowed |

The **omit** list takes the same three fields and is switched on with its own box.

## Running it

**Scan** searches the content of the files in the listed folders. There is no engine
to choose here: there is no server to ask, so the folder is read directly, and every
option is available.

The result opens in [Sources Scan Results]({{ site.baseurl }}/tools/sources-scan-results/),
in a tab labeled as a local scan so two tabs from the two sides are never confused.

## When the answer differs from the server

If a local scan and a server scan disagree, the folder and the library are not the
same. That is worth knowing on its own, and
[Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/) is where it gets
settled.

## Related

- [Scan Server Sources]({{ site.baseurl }}/tools/scan-server-sources/)
- [Sources Scan Results]({{ site.baseurl }}/tools/sources-scan-results/)
