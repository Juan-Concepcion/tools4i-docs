---
title: Jobs Manager
layout: default
parent: Jobs
nav_order: 1
permalink: /tools/jobs-manager/
---

# Jobs Manager
{: .no_toc }

Finding one job among the thousands a system is running, and acting on it or on
several at once.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Jobs Manager**.

## The filters

**Search** asks the server for the jobs matching the criteria. Everything is optional,
and an empty box means "all".

| Filter | What it takes |
|---|---|
| **Status** | Where the jobs are: running now, waiting on a job queue, or finished and sitting on an output queue |
| **Run status** | One run status. **MSGW** is the one to look for when a job is stuck waiting for an answer |
| **Type** | Interactive, batch, subsystem monitor, and the rest |
| **Subsystem** | `QBATCH`, `QINTER`, whichever |
| **Job number** | The six digits, when you already know them |
| **User** | The profile the job belongs to |
| **Job name** | |
| **Entered the system** between two moments | Tick the box beside it to use the range. Left unticked, whatever the boxes hold is ignored. Leaving the second one empty means "up to now" |

### The extra-detail pass

One checkbox adds enhanced **Type**, **Entered time** and **CPU and resource** columns
for active jobs.

It is off by default for a reason: it gathers detailed per-job data and can slow the
response noticeably on a system with many jobs. Use it when you are deciding **which**
of two jobs is hurting, not when you are only trying to find one.

## The result

The table carries the job, its user, its number, its status and its subsystem, with a
quick filter under each heading and sortable columns. **Reset filters** clears the
quick filters without touching the search criteria, and the fold control hides the
whole filter block once the list is up.

Run status is worth reading rather than skimming: `MSGW` is waiting for a message
reply, `LCKW` is waiting for a lock, `DSC` is disconnected, `HLD` is held.

## The right-click menu

### On one job

| Entry | What it opens or does |
|---|---|
| **Job info** | [Job Info]({{ site.baseurl }}/tools/job-info/) for this job |
| **Job log** | [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/) |
| **Spooled files** | The spooled files this job produced |
| **User info** | [User Info]({{ site.baseurl }}/tools/user-info/) for the profile it runs under |
| **Change job...** | The dialog below |
| **Hold**, **Release** | |
| **End (controlled)...**, **End (immediately)...** | Both ask first |

### With several jobs selected

The same actions, with the count in the label, so you can hold, release, end or pull
the job logs of a set in one go.

## Change job

The dialog changes only what you fill in. Anything left empty keeps its current value:

| Field | |
|---|---|
| **Run priority** | 1 (highest) to 99 |
| **Job queue priority** | 0 to 9 |
| **Output queue** | Library and name, for the job's spooled files |

**Apply** makes the change; **Cancel** closes without touching the job.

## Related

- [Job Info]({{ site.baseurl }}/tools/job-info/)
- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
- [Job Description Info]({{ site.baseurl }}/tools/job-description-info/)
