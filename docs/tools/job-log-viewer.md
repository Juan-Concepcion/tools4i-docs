---
title: Job Log Viewer
layout: default
parent: Jobs
nav_order: 3
permalink: /tools/job-log-viewer/
---

# Job Log Viewer
{: .no_toc }

A job log as a table you can work through, from a live job, from a file saved earlier,
or from plain text somebody sent you.
{: .fs-5 .fw-300 }

For the whole job, from somebody else's evidence to a ticket that answers itself, read
the guide [A job log with no connection]({{ site.baseurl }}/guides/job-log/).
{: .fs-3 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Job Log Viewer**, or jump straight from the
[Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/).

The job box takes `number/user/name`. A bare job number works when only one job has
it.

| Button | What it does |
|---|---|
| **Get info** | Reads the log from the server. It opens in a tab of its own, so several jobs can be compared side by side |
| **Save** | Saves the log shown as a snapshot |
| **Open...** | Opens a log saved earlier |
| **Import...** | Imports a log downloaded as plain text with another tool. The job does not have to exist any more, and neither does the system it ran on |

Each log gets its own tab, named after the job, and a tab from a file is marked as
such so it is never confused with a live one.

## The table

Time, message ID, severity, type, the program it came from, and the text, colored by
severity: errors in red, warnings in amber.

The summary line above it says the job, the user, the name, the message count, the
error count and when the reading was taken. For a log opened from a file it also says
which file it came from.

A job log of any size scrolls smoothly, right to the last message. In a log that large
each message is kept to one line so the rows line up, with the rest of a long one in
its tooltip and in the detail the row opens.

## Narrowing it

| Control | What it does |
|---|---|
| **Quick filters**, under each heading | Offered from the values present in **this** log, not from a list of everything that exists |
| **Time window** | Tick the box, then set either end. Only messages issued inside it are shown |
| **Search** | Highlights the text and steps through the matches with the arrows. It highlights without hiding anything |
| **View details** | Opens the second-level text of every message at once |

The match counter covers **the filtered list**, so filtering to the CPF messages and
then searching inside them counts what you are looking at, not the whole log. The
search also looks inside the second-level text, and opens a row by itself when the
match is in there.

## The second-level text

Click a row that has help, or switch on **View details** for all of them.

The help is laid out the way the system shows it: Cause and Recovery apart, and a
recovery written as a list of steps shown as a list of steps, one per line.

## Keeping it

**Save** writes the log exactly as it came. Reopening it rebuilds the whole table: the
job and its counts, the time of the reading, and every message with its second-level
text intact.

## Related

- [Job Info]({{ site.baseurl }}/tools/job-info/)
- [Message Queue Viewer]({{ site.baseurl }}/tools/message-queue-viewer/)
