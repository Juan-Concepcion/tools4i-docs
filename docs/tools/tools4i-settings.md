---
title: Tools4i Settings
layout: default
parent: Settings
nav_order: 1
permalink: /tools/tools4i-settings/
---

# Tools4i Settings
{: .no_toc }

Every setting the extension contributes, in one searchable form, including the two
protections worth setting up on the first day.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Tools4i Settings**. The same settings are also
in the VS Code settings editor, filtered to this extension.

## How the page works

The **search** box at the top shows only the settings matching what you type, looking
in the label, the description **and the setting key**, so a key quoted in a bug report
finds its control.

**Nothing is saved until you press Save.** **Reload** reads the settings again and
discards anything changed here but not saved.

## The sections

| Section | What it covers |
|---|---|
| **Startup** | What opens when the window does |
| **Duplicate Spooled File** | How copying a spooled file is done, and the library a deployed helper goes in |
| **Library Compile Order** | The naming rules used to work out what each member builds |
| **Scan Server Sources** | The search engine and its defaults |
| **Compile Local Source** | How a local source is staged before Run Action on Server, and where its compile errors are shown |
| **Object and Sources** | The reconciliation defaults and the skip rules |
| **Review Authority Failures** | The profiles excluded by default |
| **Diagnostics** | What is written to the Tools4i log |
| **PDF creation** | The local converter, when you use one |
| **Data Model: Items** | The color and shape each item type gets in a diagram |
| **Data Model: Sensitivity** | The classification levels |
| **Local Project** and **Server Library Project** | Where a project's libraries are kept |
| **System Protection** and **Production Protection** | The two below |

## Restore defaults, by section

Each section can go back to what Tools4i ships with.

Doing that also keeps that section **following later improvements** to those defaults,
instead of freezing it at today's values. That is the one to use when a setting was
changed once, for a reason nobody remembers.

Names you chose by hand are left alone, so restoring the Data Model section does not
rename your item types.

## Protected libraries

Libraries the extension must never modify. Its own copy, rename, delete, change-text,
deploys, sync writes and editor saves are blocked there, and their source members open
read-only.

This is the cheapest insurance in the product. Put production in it before you do
anything else.

## Production protection

Any connection whose host name or IP is **not** in your list of development systems is
treated as production.

Destructive changes, object creation, uploads and sync writes, editor saves and
deploys can each be blocked independently, and the interface shows a red production
warning so you always know which kind of system you are on.

The list is of **development** systems, not production ones, on purpose: a system you
forgot to list is treated as production, which is the safe way for the mistake to go.

## Related

- [About Tools4i]({{ site.baseurl }}/tools/about-tools4i/)
