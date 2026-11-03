---
title: Job Info
layout: default
parent: Jobs
nav_order: 2
permalink: /tools/job-info/
---

# Job Info
{: .no_toc }

One job across eleven tabs, saved as a snapshot, and openable from a printed report
when you have no access to the system at all.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Job Info**, or jump to it from the
[Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/).

Four buttons sit on the bar:

| Button | What it does |
|---|---|
| **Get info** | Reads the job from the server. **Only the Attributes tab loads now**; each other tab is fetched the first time you open it |
| **Save** | Saves everything loaded, the attributes and the tabs you have opened, as a snapshot |
| **Open...** | Opens a snapshot saved earlier |
| **Import DSPJOB file** | Imports a downloaded job report as text and fills every tab the report contains, with no connection |

The lazy loading is deliberate. Asking for eleven sections of a job is expensive, and
most questions are answered by two of them.

## The tabs

| Tab | What it holds | The question it answers |
|---|---|---|
| **Attributes** | Status, subsystem, dates, priorities and limits | What is this job, and is it still running |
| **Job Log** | The messages the job has issued, newest last | What did it say before it went wrong |
| **Call Stack** | What the job is running right now, innermost call first | Where is it stuck |
| **Library List** | The libraries **this job** searches, in order, plus its current library | Why did a call resolve to the wrong copy |
| **Open Files** | The files the job has open at this moment, with their state | Is it still reading, and from where |
| **Activation Groups** | The groups in the job, and what is running in each | Why did a scoped override or a commitment definition not apply |
| **Locks** | The objects this job holds a lock on | Who is holding the file another job is waiting for |
| **Definition** | The job description and the values the job **started** with | Was it submitted the way we thought |
| **File Overrides** | The overrides in force | Why did it write to a file nobody expected |
| **Commitment Control** | Commitment definitions and their pending changes | Is there an uncommitted transaction sitting there |
| **DSPJOB Report** | The full report as text | Anything the tabs above do not break out |

Three of them carry most of the hard answers:

- **Library List** describes the job you are looking at, not the list your own session
  is using. That is the answer when a program resolved to the wrong copy of itself.
- **Definition** is what the job **started** with, before anything changed it, so a
  difference between it and the Attributes tab is somebody or something changing the
  job mid-flight.
- **Locks** and **Open Files** read together answer the stuck-job question that has
  two jobs in it: this one holds the lock, that one is waiting.

Four tabs carry a box of their own: **Job Log**, **Call Stack** and **DSPJOB Report**
highlight the text and step through the matches, and **Definition** filters its
attributes down to the ones whose name or value contains what you type. The call stack
box takes a program name, a procedure or a statement number.

The Job Log tab also carries a **Job Log Viewer** button, which opens the same log in
the [full viewer]({{ site.baseurl }}/tools/job-log-viewer/) when the messages need
filtering, searching or saving rather than reading.

## Reading a long call stack

The Call Stack tab has one option worth knowing: **hide the system frames**. It drops
the command entry, the menus and the runtime a job passes through, leaving only your
own programs, and **the frame numbers keep their real position** so nothing is
renumbered to look tidier than it is.

On a job deep inside an application that is the difference between forty frames and
the six that are yours.

## Acting on the job

From here the job itself can be **held**, **released**, **ended now**, and its
**spooled files** listed, so a job you came to read does not need a trip back to the
[Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/) to be acted on.

## Refresh, per tab

Every tab has its own **Refresh**, because a running job changes as you watch it.
Refreshing the Attributes tab reloads the job section; refreshing the report re-runs
the whole thing and reloads the tabs that come from it.

## Answering a job that is waiting

When the job sits on an inquiry, the message is shown with three choices:

- **Send reply**, which answers the message so the job can carry on. It acts on the
  job immediately.
- **Open message queue**, which opens the queue in the
  [Message Queue Viewer]({{ site.baseurl }}/tools/message-queue-viewer/).
- **Close**, which goes back without answering. The job stays waiting.

## Reading a job you cannot reach

**Import DSPJOB file** takes the text of a job report produced by the system's own
display command sent to a printer. Every tab the report contains is filled, offline.

That is the case where somebody sends you the evidence instead of the access.

## Related

- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
- [Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/)
- [Job Description Info]({{ site.baseurl }}/tools/job-description-info/)
