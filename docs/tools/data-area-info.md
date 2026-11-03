---
title: Data Area Info
layout: default
parent: Database
nav_order: 4
permalink: /tools/data-area-info/
---

# Data Area Info
{: .no_toc }

What a `*DTAARA` holds right now, with each field copied by a click.
{: .fs-5 .fw-300 }

## What it is for

Many applications keep their configuration and their run switches in data areas. So
the question "is the program wrong, or was it told to behave that way" is answered
here, and usually in a few seconds.

## Opening it

**Tools4i** in the Activity Bar, then **Data Area Info**.

Both boxes are required: the **library** and the **name**. There are no wildcards
here, because it reads one data area at a time.

**Show info** reads it.

## What it shows

Type, length, decimal positions, the current value, and the text.

Each one copies with a click, which matters when the value is a 40-character string of
flags somebody has to paste into a ticket.

## Related

- [Job Description Info]({{ site.baseurl }}/tools/job-description-info/), the other
  place an unexplained behavior usually turns out to come from.
- [Journal Entries Viewer]({{ site.baseurl }}/tools/journal-entries-viewer/), which
  reads a journaled data area's history.
