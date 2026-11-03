---
title: About Tools4i
layout: default
parent: Settings
nav_order: 2
permalink: /tools/about-tools4i/
---

# About Tools4i
{: .no_toc }

Version, author, license, and the Code for IBM i build it is running on.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **About Tools4i**.

## Why the Code for IBM i build is on there

Tools4i runs on top of Code for IBM i and uses its connection. When something behaves
differently on two machines, those two versions are the first thing to compare, and
the first thing to put in a bug report.

## The two buttons

| Button | What it opens |
|---|---|
| **Tools4i Settings** | The [settings page]({{ site.baseurl }}/tools/tools4i-settings/) |
| **Diagnostics Log** | The Tools4i output channel |

The diagnostics log is the one to reach for when something failed without saying why.
It records the calls Tools4i makes to the server, with what it sent and what came
back, at the level of detail you set in the Diagnostics section of the settings.

One thing to know when reading it: every IBM i extension in the window shares one
connection, and a call whose origin cannot be told apart is **kept** rather than
dropped, so the log can show traffic that is not Tools4i's. The entries marked as
actions are the ones that came from this extension.

## What to copy into a report

The issue template asks for the Tools4i version, the Code for IBM i version and the
editor build. All three are here.

## Related

- [Report a problem](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose)
- [Tools4i Settings]({{ site.baseurl }}/tools/tools4i-settings/)
