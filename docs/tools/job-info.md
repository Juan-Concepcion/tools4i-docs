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

| Tab | What it holds |
|---|---|
| **Attributes** | Everything the system records about the job: status, subsystem, dates, priorities and limits |
| **Job Log** | The messages the job has issued, newest last |
| **Call Stack** | What the job is running right now, innermost call first. The place to look when a job seems stuck |
| **Library List** | The libraries **this job** searches, in order, plus its current library |
| **Open Files** | The files the job has open at this moment |
| **Activation Groups** | The activation groups in the job, and what is running in each |
| **Locks** | The objects this job holds a lock on. Where to look when another job is waiting |
| **Definition** | The job description and the values the job started with, before anything changed them |
| **File Overrides** | The overrides in force, which redirect a file the program opens to a different one |
| **Commitment Control** | Commitment definitions and their pending changes |
| **DSPJOB Report** | The full report as text, for anything the tabs do not break out |

Two of them answer most of the hard questions. **Library List** describes the job you
are looking at, not the list your own session is using, which is the answer when a
program resolved to the wrong copy. **File Overrides** is the answer when a program
wrote to a file nobody expected.

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
