---
title: Home
layout: default
nav_order: 1
permalink: /
---

# Tools4i

A suite of IBM i developer tools for Visual Studio Code, built on top of
[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi).

Tools4i adds the tools a day of work keeps asking for: finding objects and source,
searching inside the code, looking at the data, modeling and documenting the database,
managing jobs and spooled files, editing IBM i objects, and working out what a change
would affect. From the editor, and against the server.
{: .fs-5 .fw-300 }

[Install from the Marketplace](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i){: .btn .btn-primary }
[Install from Open VSX](https://open-vsx.org/extension/tools4i/tools4i){: .btn }
[Report a problem](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose){: .btn }

---

## Start with a job, not a tool

Each guide takes one job and walks it from the first click to the result.

| Guide | The question it answers |
|---|---|
| [Modeling an inherited database]({{ site.baseurl }}/guides/data-model/) | How do I understand the data of an application nobody documented |
| [What a change would break]({{ site.baseurl }}/guides/change-impact/) | What breaks if I change this file, or this procedure |
| [A job log with no connection]({{ site.baseurl }}/guides/job-log/) | How do I read a job log from a system I cannot reach |
| [A file described by its program]({{ site.baseurl }}/guides/program-described-file/) | How do I read a file whose fields live only in the program |

## Every panel, section by section

The same sections, in the same order, as the **Tools4i** view in the Activity Bar. One
page per panel: what it is for, how to open it, how to work it, and what it will not do.

### [Navigate]({{ site.baseurl }}/tools/navigate/)

- [Navigate Server]({{ site.baseurl }}/tools/navigate-server/)
- [Navigate Local]({{ site.baseurl }}/tools/navigate-local/)

### [Search]({{ site.baseurl }}/tools/search/)

- [Scan Server Sources]({{ site.baseurl }}/tools/scan-server-sources/)
- [Scan Local Sources]({{ site.baseurl }}/tools/scan-local-sources/)
- [Sources Scan Results]({{ site.baseurl }}/tools/sources-scan-results/)

### [Compare and sync]({{ site.baseurl }}/tools/compare-and-sync/)

- [Sync Local Project]({{ site.baseurl }}/tools/sync-local-project/)
- [Sync Server Library]({{ site.baseurl }}/tools/sync-server-library/)

### [Transfer]({{ site.baseurl }}/tools/transfer/)

- [Upload Local Project]({{ site.baseurl }}/tools/upload-local-project/)
- [SavF Manager]({{ site.baseurl }}/tools/savf-manager/)

### [Binding directories]({{ site.baseurl }}/tools/binding-directories/)

- [Binding Directory Editor]({{ site.baseurl }}/tools/binding-directory-editor/)
- [Binding Directory Sync]({{ site.baseurl }}/tools/binding-directory-sync/)

### [Message files]({{ site.baseurl }}/tools/message-files/)

- [Message File Editor]({{ site.baseurl }}/tools/message-file-editor/)

### [Spooled files]({{ site.baseurl }}/tools/spooled-files/)

- [Spooled Files Manager]({{ site.baseurl }}/tools/spooled-files-manager/)
- [Dump Files Viewer]({{ site.baseurl }}/tools/dump-files-viewer/)

### [Jobs]({{ site.baseurl }}/tools/jobs/)

- [Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/)
- [Job Info]({{ site.baseurl }}/tools/job-info/)
- [Job Log Viewer]({{ site.baseurl }}/tools/job-log-viewer/)
- [Job Description Info]({{ site.baseurl }}/tools/job-description-info/)
- [Message Queue Viewer]({{ site.baseurl }}/tools/message-queue-viewer/)

### [Database]({{ site.baseurl }}/tools/database/)

- [Stored Procedures Manager]({{ site.baseurl }}/tools/stored-procedures-manager/)
- [Native Query Info]({{ site.baseurl }}/tools/native-query-info/)
- [Journal Entries Viewer]({{ site.baseurl }}/tools/journal-entries-viewer/)
- [Data Area Info]({{ site.baseurl }}/tools/data-area-info/)
- [File Viewer]({{ site.baseurl }}/tools/file-viewer/)

### [Data model]({{ site.baseurl }}/tools/data-model/)

- [Data Model Extractor]({{ site.baseurl }}/tools/data-model-extractor/)
- [Data Model Editor]({{ site.baseurl }}/tools/data-model-editor/)
- [Data Model Viewer]({{ site.baseurl }}/tools/data-model-viewer/)
- [Data Model Dictionary]({{ site.baseurl }}/tools/data-model-dictionary/)
- [Data Model Comparison]({{ site.baseurl }}/tools/data-model-comparison/)

### [Object references]({{ site.baseurl }}/tools/object-references/)

- [Programs Level Check Analyzer]({{ site.baseurl }}/tools/programs-level-check-analyzer/)
- [Native Query Level Check Analyzer]({{ site.baseurl }}/tools/native-query-level-check-analyzer/)
- [Object Change Impact Analysis]({{ site.baseurl }}/tools/object-change-impact-analysis/)
- [Library Compile Order]({{ site.baseurl }}/tools/library-compile-order/)
- [Procedure Change Impact Analysis]({{ site.baseurl }}/tools/procedure-change-impact-analysis/)
- [Object and Sources]({{ site.baseurl }}/tools/object-and-sources/)
- [Programs Signatures Analyzer]({{ site.baseurl }}/tools/programs-signatures-analyzer/)

### [System]({{ site.baseurl }}/tools/system/)

- [PTF Status]({{ site.baseurl }}/tools/ptf-status/)

### [Users]({{ site.baseurl }}/tools/users/)

- [User Info]({{ site.baseurl }}/tools/user-info/)
- [Review Authority Failures]({{ site.baseurl }}/tools/review-authority-failures/)

### [Settings]({{ site.baseurl }}/tools/settings/)

- [Tools4i Settings]({{ site.baseurl }}/tools/tools4i-settings/)
- [About Tools4i]({{ site.baseurl }}/tools/about-tools4i/)

### [From the editor]({{ site.baseurl }}/tools/from-the-editor/)

A single page: no panel of its own, so it has no list under it.

## Before anything else

Tools4i needs Code for IBM i and an active connection. It installs Code for IBM i for
you as a dependency, and it asks for no account, no license key and nothing installed on
the server. The whole picture is in
[INSTALLATION.md](https://github.com/Juan-Concepcion/tools4i-docs/blob/main/INSTALLATION.md),
and what it does and does not do with your data is in
[SECURITY.md](https://github.com/Juan-Concepcion/tools4i-docs/blob/main/SECURITY.md).

## Something missing, something wrong

A page that skips the step you were stuck on is a bug like any other.
[Open an issue](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose) and
say which page and which step.
