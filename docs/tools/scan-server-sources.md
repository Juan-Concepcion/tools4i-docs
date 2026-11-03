---
title: Scan Server Sources
layout: default
parent: Search
nav_order: 1
permalink: /tools/scan-server-sources/
---

# Scan Server Sources
{: .no_toc }

Content search across the source members of several libraries at once, built so that a
search with four conditions still reads as four decisions.
{: .fs-5 .fw-300 }

<details markdown="block">
  <summary>On this page</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Opening it

**Tools4i** in the Activity Bar, then **Scan Server Sources**.

## The search terms

Type the text in the box and press **Add**. The term joins the list below as a chip,
and a chip can be removed on its own.

Each chip carries its own verdict, chosen beside the box:

- **Matches**, which keeps the lines that include it,
- **Does NOT match**, which keeps the lines that do not.

That is what makes the second question practical: not "where is this field used", but
"where is this field used **without** the new procedure being called".

### How the terms combine

| Mode | What it means |
|---|---|
| **All terms** | A member matches only if every term appears somewhere in it, on any line |
| **Same line** | Stricter: every term has to appear together on one line. Use it when the terms belong to the same statement |
| **Any term** | Widest: a member matches as soon as any one term is found |

Two switches sit with them:

- **Case sensitive**, to match the exact upper and lower case.
- **Regular expressions**, to treat the terms as patterns instead of plain text.

### The column range

By default the whole line is searched, wherever the text sits. Switch to a **range**
and give a first and last column, which is what fixed-format sources need: a field
always sits in the same positions, and the comment area does not have to be read at
all. The default range is 1 to 100.

## Where to look, and where not to

The **targets** are added the same way the terms are, as a list you build up. Each one
is a library, a source file, a member and a type, and each accepts wildcards:

| Field | Default | Example |
|---|---|---|
| Library | | `MYLIB*` |
| Source file | `Q*` | covers the usual `QxxxSRC` naming |
| Member | `*` | `MY*` |
| Type | `*` | `RPGLE`, `CLLE`, `SQLRPGLE` |

The **omit** list is built in the same shape, and switched on with its own box. It is
the fastest way to keep a work library, or an old copy of everything, out of a scan
that otherwise has to cover the whole system.

## The two engines

The gear button beside the options chooses how the source is searched. Each way offers
different options, and **the panel shows only the ones that apply**, so a search always
runs the way it reads on screen.

| Engine | What it does | Options |
|---|---|---|
| **Unix Search** | Reads each source member as text and searches it | Everything above: several terms, terms to exclude, regular expressions, the column range |
| **IBM i Native Search** | Has the server search its own source | One plain-text term, and it is several times faster over a large library |

## Running it

**Scan** reads the members on the server and searches their content. Scanning many
libraries takes a while, and the status line says where it has got to.

The result opens in [Sources Scan Results]({{ site.baseurl }}/tools/sources-scan-results/),
in a tab of its own.

## Related

- [Scan Local Sources]({{ site.baseurl }}/tools/scan-local-sources/)
- [Sources Scan Results]({{ site.baseurl }}/tools/sources-scan-results/)
