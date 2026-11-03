---
title: What a change would break
layout: default
parent: Guides
nav_order: 2
permalink: /guides/change-impact/
---

# What a change would break
{: .no_toc }

You are about to add a field to a file, change a record format, or rebuild a service
program. On a system where nobody can list everything that touches it, the usual way to
find out what breaks is to ship the change and wait for the phone. This guide is the
other way.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Start from the file, not from the program

Open the **File Viewer** on the file you are about to change and read the
**Dependents** tab. It lists the database relations built over it: every logical file,
view and index, each with its object type, description and SQL long name.

That answers "who breaks if I change this record format" before the change, instead of
having the compiler answer it afterwards. It is the cheapest check here and it takes
one click.

## Ask what the change reaches

**Object Change Impact Analysis** takes an object and reports what a change to it would
affect:

- dependents that have to be recreated,
- programs that have to be recompiled,
- stored procedures affected,
- and the **rebuild plan in the order it has to run**.

The order is the part people underestimate. Recompiling the right objects in the wrong
order produces a second round of failures that look like new problems.

Optionally it also walks the call graph, to show who calls the programs that need
recompiling. Read that part as context, not as a work list.

## Find the programs that will level-check

A program compiled against an old record format does not fail at compile time. It fails
at run time, in front of a user, with a level check.

**Programs Level Check Analyzer** lists the programs that will level-check against the
files in your data libraries, in three views:

1. the level-id comparison, with an "affected only" filter that also surfaces the cases
   where level checking is simply turned off,
2. the resulting list of programs to recompile,
3. the files involved.

The "turned off" cases deserve a look of their own. A program that does not level-check
does not fail. It reads the record with the old layout and writes whatever that
produces.

**Native Query Level Check Analyzer** answers the same question for `*QRYDFN` queries,
which fail for the same reason and are usually remembered last.

## For a service program, ask about the signature

Rebuilding a service program with a changed export list moves its signature, and every
program bound to the old one fails at activation, not at compile.

**Programs Signatures Analyzer** lists the callers that will fail because the service
program they were bound to no longer carries the signature they hold, in three views:
the comparison, the callers to rebind, and the service programs involved.

For a single exported procedure, **Procedure Change Impact Analysis** gives every
module, service program and program to recompile, in order.

Read one caveat on that tool. **Confirm in source** reads the sources of the objects
bound directly to the one holding the procedure and reports which of them name it. A
compiled object cannot answer that question, so a miss means there is no explicit
evidence in the source, never proof that the procedure is unused.

## Rebuild in an order that works

**Library Compile Order** lists every source member of a library in a dependency-safe
build order: files, then modules, then service programs, then programs. Open or copy a
member's source from there, or run a compile action on the ones you select.

If your change crosses libraries, build the list for each one and keep the same order
between them.

## Check the sources match the objects first

Any of this is worth less if the source you are about to compile is not the source the
object was built from. **Object and Sources** reconciles the two: objects with no
source, sources with no object, and stale objects, with skip rules you configure for
the cases your shop treats as normal.

Running it once before a large change saves the particular afternoon where a
recompilation quietly reverts a fix nobody promoted.

## A sensible order for all of it

1. **Dependents** on the file, to see the database side.
2. **Object Change Impact**, for the rebuild plan.
3. **Object and Sources**, to be sure you are compiling what you think.
4. Make the change.
5. **Programs Level Check** and **Native Query Level Check**, for what the change
   invalidated.
6. **Signatures** or **Procedure Change Impact**, if a service program moved.
7. **Library Compile Order**, to rebuild in order.

## Two of these are in beta

Procedure Change Impact Analysis and Programs Signatures Analyzer are marked `*BETA` in
the side bar. They are usable and in daily use, and their results should be reviewed
before you act on them rather than taken as a complete list.
