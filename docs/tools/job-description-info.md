---
title: Job Description Info
layout: default
parent: Jobs
nav_order: 4
permalink: /tools/job-description-info/
---

# Job Description Info
{: .no_toc }

What a `*JOBD` actually says, in a grouped grid, for the day a program behaves
differently depending on how it was submitted.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **Job Description Info**.

| Field | What it takes |
|---|---|
| **Library** | The library to look in. Wildcards allowed, and `*ALL` searches every library on the system |
| **Name** | The job description. Wildcards allowed, such as `MY*` |

**Get info** looks up everything that matches and shows the attributes of the first
one found. When the name matched several, the **Match** box lists them all: pick one
and its attributes replace what is on screen.

Searching `*ALL` for a name pattern is the way to answer "how many job descriptions on
this system still point at that library".

## Reading the result

The attributes come grouped rather than as one long list. The **Filter** box above
them shows only the attributes whose name or value contains what you type, which is
how you get from eighty attributes to the one you came for.

The two that answer most questions:

- **The library list** the job starts with, plus its current library. When the same
  program behaves differently depending on how it was submitted, this is almost always
  why.
- **The message logging level**. A low level is why the job log somebody sent you has
  nothing useful in it.

The rest covers the job queue and its priority, the output queue, the accounting code,
the hold and date attributes, and the inquiry message reply.

## Keeping it

**Save** writes the loaded job descriptions as a snapshot, and **Open...** brings one
back.

Worth doing before somebody changes the object: the evidence of what it used to say
disappears with it.

## Related

- [Job Info]({{ site.baseurl }}/tools/job-info/), for what a running job ended up with
  rather than what it started from.
- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
