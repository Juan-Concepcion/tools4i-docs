---
title: User Info
layout: default
parent: Users
nav_order: 1
permalink: /tools/user-info/
---

# User Info
{: .no_toc }

Everything a user profile carries, in a grouped grid, so "why can this user do that"
is answered in one place.
{: .fs-5 .fw-300 }

## Opening it

**Tools4i** in the Activity Bar, then **User Info**.

The **name** box takes one profile, or a pattern ending in `*`. When several match,
the **Match** list fills: choose one and its attributes replace what is on screen.

**Get info** reads the profile and shows its attributes, group memberships and
special authorities.

## Reading the result

The attributes come grouped rather than as one long list, and the **Filter** box above
them narrows by name or value, which is how you get from eighty attributes to the one
you came for.

What is in there:

- class and special authorities,
- group profile and supplemental groups,
- initial program and initial menu,
- current library,
- limit capabilities,
- password and expiration state,
- sign-on attempts and status,
- storage used,
- and when the profile was last used.

The last two answer the housekeeping questions: who is still here, and who has been
gone for three years with a profile still enabled.

## Why it is usually enough

Most authority questions are not about the object. They are about the profile: a group
nobody remembered, a special authority granted for one afternoon in 2019, limit
capabilities set in a way that changes what the initial program can do.

## Keeping it

**Save** writes the loaded information as a snapshot and **Open...** brings it back,
which is what an audit answer usually needs to be.

## Related

- [Review Authority Failures]({{ site.baseurl }}/tools/review-authority-failures/)
- [Jobs Manager]({{ site.baseurl }}/tools/jobs-manager/)
