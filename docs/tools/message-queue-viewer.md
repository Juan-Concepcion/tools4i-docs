---
title: Message Queue Viewer
layout: default
parent: Jobs
nav_order: 5
permalink: /tools/message-queue-viewer/
---

# Message Queue Viewer
{: .no_toc }

A message queue browsed, filtered, answered and cleared, with the help text laid out
the way the system lays it out.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Message Queue Viewer**.

Give it the **library** (`*LIBL` searches the job's library list) and the **name**,
such as `QSYSOPR` for the system operator queue. **Get info** reads the messages that
match the filters.

## The filters, applied when you read

These narrow what is **read from the server**, so they take effect when you press
Get info, not as you type:

| Filter | What it takes |
|---|---|
| **From user** | Only messages sent by that profile |
| **From job** | Only messages whose sending job name contains the text |
| **From program** | Only messages whose sending program name contains the text |
| **Text** | Only messages whose text contains this. Free text, left exactly as typed |
| **Date range** | Tick the box to use it. Leaving the second end empty means "up to now" |
| **Max rows** | 2000 by default. A queue like `QSYSOPR` can hold tens of thousands; a smaller number returns and draws faster |

## The filters applied to what is already on screen

These need no new read:

- **Search** highlights the text in the messages already loaded and steps through the
  matches with the arrows. It keeps every row: to narrow the list, use the filters
  above and read again.
- **Show 2nd Level Message** opens the help on every row at once.
- **Inquiries only** and **Unanswered only**. Together they answer "what is waiting on
  somebody right now".
- A quick filter under each column heading.

## The table

Time, message ID, type, severity, the sending user, the sending job and the sending
program, then the text, colored by severity. The list fills the panel and grows with
the window.

Click a row to open its help underneath; double-click to open the detail pane, which
shows every field of the message, its key, and its second-level text.

## The second-level help

Laid out the way the system shows it: Cause and Recovery apart, and a numbered list of
reason codes or recovery steps shown as a list, one per line.

## Replying to an inquiry

An unanswered inquiry can be answered here. The detail pane offers:

- the replies the message itself accepts, as buttons, read out of its own help text,
  so you are not guessing which single letter the program expects,
- a box to type the answer in,
- **Send reply**, which acts on the server immediately so the waiting job can carry
  on,
- **Close**, which goes back without answering. The job stays waiting.

## Clearing

**Remove all except unanswered** clears what has been seen and leaves the unanswered
inquiries in place, because clearing one of those would leave a job waiting forever on
an answer nobody will give.

## Queue details, and keeping it

**Queue details** shows the queue object's own attributes.

**Save** writes the messages as a snapshot and **Open...** brings one back, which is
the simplest way to attach evidence to a ticket.

## Related

- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
- [Message File Editor]({{ site.baseurl }}/tools/message-file-editor/)
