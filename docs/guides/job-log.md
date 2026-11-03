---
title: A job log with no connection
layout: default
parent: Guides
nav_order: 3
permalink: /guides/job-log/
---

# A job log with no connection
{: .no_toc }

Somebody sends you the evidence instead of the access: a job log from a system you have
no profile on, pasted into a mail, or a printed job report attached to a ticket. This
guide is about reading all of it in the same table, and about leaving evidence behind
in a form the next person can open.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Three ways in

The **Job Log Viewer** opens a log from three places, and what you get afterwards is
the same table in all three cases.

| Where it comes from | How |
|---|---|
| A job on the system you are connected to | Type the job, or jump straight from the Jobs Manager |
| A log saved earlier, from any system | **Open**, and pick the saved file |
| A log someone downloaded as plain text with another tool | **Import**, and pick the text file |

The second and third need no connection at all. The job does not have to exist any
more, and neither does the system it ran on.

## Reading a long log without drowning

A job log of any size scrolls smoothly, right to the last message. These are the
controls worth knowing before you start scrolling:

- **A time window.** Narrow the log to the minutes around the failure, which is usually
  the only part anybody needs.
- **Per-column filters.** Filter by message ID, by type, or by severity, offered from
  the values actually present in that log rather than from a list of everything that
  exists.
- **Search with next and previous.** The counter covers the filtered list, so filtering
  to the CPF messages and then searching inside them gives a count of what you are
  looking at, not of the whole log.
- **Color by severity**, so the errors are findable without filtering at all.

## The second-level text, laid out the way the system shows it

Expand one message, or switch on the details to open all of them at once.

The help arrives from the system with its own layout instructions in it, and those are
honored here: the Cause and the Recovery sit apart, and a recovery written as a list of
steps is shown as a list of steps, one per line, the way it reads on a green screen.

The search looks inside that text too, so a word that only appears in the help of a
message still finds the message.

## Leaving the evidence behind

**Save** writes the log, exactly as it came, to a file you can keep with the ticket.
Reopening it later rebuilds the whole table: the job, the counts, the time of the
reading, and every message with its second-level text.

That is the simplest way to attach evidence to a ticket that someone can still read in
six months, when the job is long gone and the system may be too.

## When you need more than the log

**Job Info** covers a single job across ten tabs: attributes, job log, call stack,
library list, open files, activation groups, locks, definition, file overrides and
commitment control. It saves as a snapshot and reopens later, the same way.

It also imports a printed job report, so a job someone captured with the system's own
report command can be studied here with no connection.

Two more that answer the questions a job log raises:

- **Job Description Info** reads a `*JOBD` and shows the library list a job starts
  with, its queues and priorities, its output queue and its logging level. It is where
  the answer usually is when the same program behaves differently depending on how it
  was submitted.
- **Message Queue Viewer** browses a message queue, expands the second-level help the
  same way, replies to inquiry messages, and clears what has been seen while
  unanswered inquiries stay protected.

## A ticket that answers itself

1. Open the job log, live or from the file you were sent.
2. Narrow it to the time window of the failure.
3. Find the first message with a severity that matters, not the last one. The last one
   is usually the consequence.
4. Expand its help and read the Cause.
5. Save the log beside the ticket.
6. If the cause points at how the job was submitted, read the job description next.
