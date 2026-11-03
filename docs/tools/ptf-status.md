---
title: PTF Status
layout: default
parent: System
nav_order: 1
permalink: /tools/ptf-status/
---

# PTF Status
{: .no_toc }

Individual PTFs or whole PTF groups, with the status each one is actually in.
{: .fs-5 .fw-300 }

## What it is for

Answering "do we have that fix" without logging on to a green screen, and answering it
with the distinction that matters: **loaded**, **applied** and **superseded** are
three different answers, and only one of them means the fix is running.

## Opening it

**Tools4i** in the Activity Bar, then **PTF Status**.

| Control | What it does |
|---|---|
| **Mode** | Lists PTFs one by one, or **PTF groups** with their overall status. It also decides what the boxes beside it filter on |
| **PTF ID** | Shows only the ones whose identifier contains this text. Blank means all |
| **Product** | Restricts to a single product, such as the operating system. Blank means all |
| **Limit** | Stops after this many rows, up to 1,000,000. 2000 by default |

**Load** reads them. Run it again after applying or removing PTFs to see the change.
**Cancel** stops a lookup, reporting nothing.

Group mode is the one to use when somebody asks whether a cumulative level is in: one
row with an overall status beats four hundred rows you then have to judge.

## Reading the result

The **Filter** box narrows across every column shown, and the columns sort.

**Export** writes the rows currently shown to CSV, with the search and the sort
applied, which is how this normally reaches whoever asked: a vendor, an auditor, or
the person planning the next maintenance window.

## Related

- [About Tools4i]({{ site.baseurl }}/tools/about-tools4i/), for the version of the
  extension and the Code for IBM i build it is running on.
